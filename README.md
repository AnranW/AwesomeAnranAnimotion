# Intro
This is AwesomeAnranSlides, built upon [Animotion](https://animotion.pages.dev). 
A preview can be found [here](https://AnranW.github.io/AwesomeAnranSlides). 

# Features
- Automatically calculated total slide number. 
    ![public/pagenumber.png]
- Automatically generated navigation bar on top, including separation into chapters. 
    ![public/navibar.png]
- Highligt current slide in navigation bar. 
    ![public/highlight.png]
- Hyperlink to corresponding slides. 
    ![public/goto.png]

Note that this project is still under development, bugs can exist and features can change. 

# Technical details
The most important modifications are in the following files: 
- src/layout.svelte : define the layout 
- src/slides.svelte : includes the scripts that implements the features
- src/config.ts : activate custom layout, etc.

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

Declare a new chapter. 
```html
<script>newChapter("Introduction")</script>
```

## Deployment
For deployment, see [Vite](https://vitejs.dev/guide/static-deploy.html). 

