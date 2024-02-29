- [Intro](#intro)
- [Features](#features)
- [Technical details](#technical-details)
- [Setup, usage, and deployment](#setup-usage-and-deployment)
  - [Setup](#setup)
  - [Usage](#usage)
  - [Deployment](#deployment)

# Intro
This is **AwesomeAnranSlides**, built upon [Animotion](https://animotion.pages.dev). 

A preview of the slides built with this template can be found [here](https://AnranW.github.io/AwesomeAnranSlides). 

# Features
## This Template
Note that this project is still under development, bugs can exist and features can change. 
- Automatically calculated total slide number.

    <img src="public/pagenumber.png" style="width:5vw">
- Automatically generated navigation bar on top, including separation into chapters. 

    ![](public/navibar.png)
- Highlight current slide in navigation bar. 

    ![](public/highlight.png)
- Hyperlink to corresponding slides. 

    <img src="public/goto.png" style="width:20vw">

## [Animotion](https://animotion.pages.dev) package
- Automatic animation.
- Better code presentation.
- Multimedia support (audios, videos, scrollable pdf...)
- And so much [more](https://animotion.pages.dev/docs)...

# Technical details
The most important modifications are in the following files: 
- [src/layout.svelte](src/layout.svelte) : define the layout 
- [src/slides.svelte](src/slides.svelte) : includes the scripts that implements the features
- [src/config.ts](src/config.ts) : activate custom layout, etc.

# Setup, usage, and deployment
## Setup
Install dependencies. 
```sh
pnpm i
```

Run the development server at http://localhost:5173/. 
```sh
pnpm run dev
```
Build and preview deploy.
```sh
pnpm run build && pnpm run preview
```

## Usage
Include the layout file in [slides.svelte](/src/slides.svelte). 
```html
<script>
    import Layout from './layout.svelte'
</script>
```

Use layout inside <Slide>. 
```html
<Layout>
    ...
</Layout>
```

Declare a new chapter with chapter name. 
```html
<script>newChapter("Chapter Name")</script>
```

## Deployment
For more details, see [Vite](https://vitejs.dev/guide/static-deploy.html). 

1. Change configuration for "base" into the name of your repository at the last line of [vite.config.ts](vite.config.ts). 
2. Go to repository **Settings->Pages->Build and deployment->Source and select** *GitHub Actions*. 

Optional: more building options can be found in the YAML file at [.github/workflows/deploy.yml](.github/workflows/deploy.yml). 

