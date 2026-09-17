---
marp: true
theme: gaia
header: "Georeferencing with IIIF : Using the Allmaps Plugin for MapLibre GL"
style: |
  section.title {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    background: #4930b800;
    color: white;
  }

  section.headline {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background: #141a5f;
    color: white;
  }

  section.normal {
    display: flex;
    flex-direction: column;
    justify-content: center;
    background: #4930b800;
    color: white;
  }

  section.normal .contents {
    flex-grow: 1;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  section.normal .contents p,
  section.normal .contents div {
    max-width: 800px;
  }

---

<!-- _class: title  -->
# Georeferencing with IIIF
## Using the Allmaps Plugin for MapLibre GL
22 September 2026 Nobutake Kamiya

---

<!-- _class: headline  -->
# What is Allmaps?
![w:300](./assets/allmaps-logo.svg)

---

<!-- _class: normal  -->

## Allmaps

<div class="contents">
<p><a href="https://allmaps.org/" target="_blank" rel="noopener noreferrer">Allmaps</a> is a project by Bert Spaan and Jules Schoonman. It provides tools for georeferencing digital images using IIIF. The project has evolved through feedback and ideas from the <a href="https://iiif.io/community/groups/maps/" target="_blank" rel="noopener noreferrer">IIIF Maps Community Group</a>.
</p></div>

---

<!-- _class: headline  -->
## Demo!

---

<!-- _class: normal -->
## Example: Exploring Dejima

<div><p>
<a href="https://kokusho.nijl.ac.jp/biblio/300136604/3?ln=ja" target="_blank" rel="noopener noreferrer">Original image (IIIF)</a><br />

<a href="https://nbtkmy.github.io/iiif-map-viewer/" target="_blank" rel="noopener noreferrer">A georeferenced historical map of Dejima</a>, combined with annotations and illustrations from other IIIF resources.
<br />
</p></div>

---


<!-- _class: headline  -->
## How does this work?

---

<!-- _class: normal  -->
## IIIF Georeference Extension

<div class="contents"><p>The IIIF Maps Community Group worked on a standard for georeferencing IIIF resources. <a href="https://iiif.io/api/extension/georef/" target="_blank" rel="noopener noreferrer">IIIF Georeference Extension</a> is one result of this work.
</p></div>

---

<!-- _class: normal  -->
## What is a Georeference Annotation?

<div class="contents"><p>
The IIIF Georeference Extension describes how to store the information needed to place an IIIF resource on a map.<br />
Basically, it connects points in an image with locations in the real world.<br />
This information is stored in a Georeference Annotation.
</p></div>



---
<!-- _class: normal -->
## Example of a Georeference Annotation

<div><p>
<a href="https://kokusho.nijl.ac.jp/biblio/300136604/3?ln=ja" target="_blank" rel="noopener noreferrer">Original image (IIIF)</a>
<br />
<a href="https://gist.github.com/NbtKmy/d5fbd40d5988843641c24398f0db6fec?short_path=3ecf7bd" target="_blank" rel="noopener noreferrer">Georeference Annotation (JSON)</a>
<br />
<a href="https://viewer.allmaps.org/?url=https%3A%2F%2Fgist.githubusercontent.com%2FNbtKmy%2Fd5fbd40d5988843641c24398f0db6fec%2Fraw%2F98a5926966a9ee3ddcee1016dd95c742be3ae2bc%2Fdejima.json" target="_blank" rel="noopener noreferrer">View it in Allmaps Viewer</a>
</p></div> 



---

<!-- _class: headline -->

## Allmaps plugin for MapLibre GL


---

<!-- _class: normal -->

## Allmaps plugin for MapLibre GL

<div><p>
The plugin loads Georeference Annotations and displays the corresponding IIIF images on a MapLibre map.<br />
Because it's MapLibre, you can add your own layers, controls, and interactions.
</p></div>


---


<!-- _class: headline -->

## How do I use the plugin?

---

<!-- _class: normal -->
## Install with npm

```shell
# In your project folder
npm i maplibre-gl @allmaps/maplibre
```

## Import the plugin
```javascript

import { WarpedMapLayer } from '@allmaps/maplibre'

```
---

<!-- _class: normal -->
## Add a WarpedMapLayer
```javascript

const annotationUrl = 'https://annotations.allmaps.org/maps/751ae05935adba4f'
const warpedMapLayer = new WarpedMapLayer()

map.on('load', () => {
  map.addLayer(warpedMapLayer)
  warpedMapLayer.addGeoreferenceAnnotationByUrl(annotationUrl)
})
```


---

<!-- _class: normal -->
## A simple example

[This repo](https://github.com/NbtKmy/allmaps_test/tree/main)

---

<!-- _class: normal -->
## What could you build?

- Historical map explorers
- Story maps
- Map comparison tools
- Annotation tools
...or what would you build?

---

<!-- _class: headline  -->
# Thank you!