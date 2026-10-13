# Inside Nemotron 3

A visual, interactive field guide to NVIDIA Nemotron 3 **Super**. Open the architecture, then follow links into Mamba-2, grouped-query attention, LatentMoE, multi-token prediction, training and inference. A searchable glossary stays alongside the lessons on desktop and opens as a drawer on smaller screens.

The site is static HTML, CSS and JavaScript. No account, API key, model download or build tool is needed. Progress is stored only in the browser's local storage. The illustrations are original and the numerical animations are explicitly labeled teaching examples.

## View locally

Open `index.html` directly in a browser, or serve the folder:

```sh
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Publish on GitHub Pages

The included workflow publishes the three site files and `.nojekyll` when `main` changes. In repository **Settings → Pages**, choose **GitHub Actions** as the build and deployment source. Private repositories require an eligible GitHub plan; otherwise make this repository public before enabling Pages.

Expected URL: https://lorenzoriano.github.io/nemtron_studt/

## Content and accuracy

- Main subject: the Nemotron 3 Super text decoder, labeled 120B-A12B.
- Exact 88-layer pattern: 40 Mamba-2, 40 LatentMoE, 8 GQA layers, counted from [NVIDIA's pinned configuration](https://huggingface.co/nvidia/NVIDIA-Nemotron-3-Super-120B-A12B-BF16/blob/a9f80fc8bdaa9ad2104cac1fd895cfa06daa8fe8/config.json).
- The router and shared expert remain full width; the routed expert path uses the 1,024-dimensional latent representation.
- KV cache growth is linear in sequence length. Quadratic scaling refers to dense all-pairs attention work over a full sequence.
- The report's 1M context capability is distinguished from the pinned config's 262,144 default.
- MTP training offsets and exported prediction module counts are distinguished because they vary across releases.
- Nano uses standard sparse MoE. Super and Ultra use LatentMoE. Later 3.5 and multimodal Omni designs are outside this guide.

Primary references, source code links and explanatory assumptions are available in the site's **Sources & scope** view. The starting Kubesimplify article is linked there; technical lessons are grounded in primary sources.

## Accessibility

Keyboard-operable navigation and controls, descriptive labels, responsive layouts, visible focus states, live simulation captions, and reduced-motion support. Use **Pause motion** to stop continuous animation; every simulation can be stepped manually.

## Editing

`app.js` holds the concept graph, glossary, source references and simulations. `styles.css` contains the responsive design. Deep links use hashes so they work under a repository subpath without server rewrite rules.
