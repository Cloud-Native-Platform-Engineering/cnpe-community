---
# parameters for website rendering options

list_pages: false
# use toc_hide to hide this section from the sidebar
toc_hide: true
---

# Platform Capability Factors

The Cloud Native Platform Engineering Community maintains and publishes this paper describing a
platform marketplace model and a set of testable capability factors that let organizations grow
internal platforms beyond a centralized bottleneck.

This is a new, evolving paper; improvements and iterations continue in the
[`latest`](./latest/) directory until a first version is tagged.

Currently, the edition in the `latest` directory is published to The Cloud Native Platform
Engineering Community's website at
[https://cloudnativeplatforms.com/whitepapers/platform-capability-factors](https://cloudnativeplatforms.com/whitepapers/platform-capability-factors).

## Figures

The figures in `latest/assets/` are exported from
[`latest/assets/capability-factors-figures.drawio`](./latest/assets/capability-factors-figures.drawio),
one tab per figure in page order (some figures also have a landscape tab). Open it in
[diagrams.net](https://app.diagrams.net/) or the draw.io desktop app; the styles are embedded, so
no shape library is needed. After editing, export the tab as PNG at 2x with a transparent background and
replace the matching file in `latest/assets/`.

A landscape tab is exported under the same name with a `-landscape` suffix. The page shows it instead of
the portrait figure through a `<picture>` source once the window can display it at about 75% of its size or
more, which keeps its labels at 10px or larger; narrower screens get the portrait figure. If a landscape
tab's size changes, set the `width`/`height` on its `<source>` to half the PNG's pixel size and its
`min-width` breakpoint to about (0.75 × width + 63) × 12 / 7 px, the window width at which the page's
content column is that wide.
