<script lang="ts">
	import { tweened } from 'svelte/motion'
	import { quadInOut } from 'svelte/easing'
	import { Presentation, Slide, Code, Step } from '@components'
	import Layout from './layout.svelte'
    import { svelte } from '@lib/languages/svelte';
</script>

<Presentation>	


	<!-- intro -->
	<Slide >
		<Layout>
			<div class="flex h-full items-center justify-center gap-[100px]">
				<div>
					<img width="400" src="manim.svg" alt="logo" />
					<p>Manim</p>
				</div>
			</div>
		</Layout>
	</Slide>

	<Slide animate>
		<Layout>
			<div class="flex h-full items-center justify-center gap-[100px]">
				<div>
					<img width="400" src="manim.svg" alt="logo" />
					<p>Manim</p>
				</div>

				<div>
					<img width="400" src="motion-canvas.svg" alt="logo" />
					<p>Motion Canvas</p>
				</div>
			</div>
		</Layout>
	</Slide>

</Presentation>
