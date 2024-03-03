<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/AnranW/AwesomeAnranAnimotion">
    <img src="public/Automation-StatusUpdatesLogo.png" alt="Logo" width="330" height="120">
  </a>

  <h3 align="center">Awesome Anran Animotion</h3>

  <p align="center">
    Awesome presentation slides for local and online use!
</div>

- [Intro](#intro)
- [Features](#features)
  - [This Template](#this-template)
  - [Animotion package](#animotion-package)
- [Technical details](#technical-details)
- [Setup, usage, and deployment](#setup-usage-and-deployment)
  - [Setup](#setup)
  - [Usage](#usage)
  - [Deployment](#deployment)
- [Troubleshooting](#troubleshooting)


# Intro
This is **AwesomeAnranAnimotion**, built upon [Animotion](https://animotion.pages.dev). 

A preview of the slides built with this template can be found [here](https://AnranW.github.io/AwesomeAnranAnimotion). 

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


## Usage
Include the layout file at the beginning of [slides.svelte](/src/slides.svelte). 
```html
<script>
    import Layout from './layout.svelte'
</script>
```

Declare a new chapter with chapter name. 
```html
<script>newChapter("Chapter Name")</script>
```

Use layout inside <Slide>. 
```html
<Layout>
    ...
</Layout>
```

Use title bars as needed: 
```html
<titlebar>
    ...
</titlebar>
```

Use "mybody" tag for centering layout as needed: 
```html
<mybody>
    ...
</mybody>
```


## Deployment
Build and preview deploy.
```sh
pnpm run build && pnpm run preview
```

1. Change configuration for "base" into the name of your repository at the last line of [vite.config.ts](vite.config.ts). 
2. Go to repository **Settings->Pages->Build and deployment->Source and select** *GitHub Actions*. 

Optional: more building options can be found in the YAML file at [.github/workflows/deploy.yml](.github/workflows/deploy.yml). 

For more details, see [Vite](https://vitejs.dev/guide/static-deploy.html). 

# Troubleshooting
- **Issue:** Any.
  - **Possible solution:** Inspect errors by pressing alt+ctl+i or opt+cmd+i to locate which slide is the problematic one. 

- **Issue:** Empty HTML content with error message like "server returned with status 404"
  - **Possible solution:** Check that the "base" is set correctly in [vite.config.ts](vite.config.ts). 

- **Issue:** Images not showing despite being in "public/" folder
  - **Possible solution:** Add or remove the slash in front of the relative path of the image files, depending on whether a slash is present at the end of "base" configuration in [vite.config.ts](vite.config.ts). 

- **Issue:** Circles on top of the slides not showing
  - **Possible reason:** JavaScript codes at the end of [slides.svelte](src/slides.svelte) was not executed to the end because of errors due to absent bug catching and assertions that are to be implemented.

- **Issue:** Layout elements missing and "Uncaught TypeError: slidesInChapter[0] is undefined"
  - **Possible reason:** This can happen if a chapter is defined but has no slides- just make sure to add some content to each slide-code-block.


