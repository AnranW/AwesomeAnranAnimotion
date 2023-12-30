<script lang="ts">
	import { Presentation, Slide } from '@components'
	import Layout from './layout.svelte'
</script>

<Presentation>	
	<script>
		let chapter=0;
		function newChapter(){
			chapter++;
		}
	</script>
	<!-- intro -->
	<Slide >
		<Layout>
			<div class="flex h-full items-center justify-center gap-[100px]">
				<div>
					<img width="400" src="manim.svg" alt="logo" />
					<p id="m">Manim</p>
				</div>
			</div>
		</Layout>
	</Slide>

	<script>newChapter()</script>
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

	<!-- to show slide number with total slide number  -->
	<script>
		const totalSlides = document.getElementsByTagName('pagenumber').length;
		for (let i = 0; i < totalSlides; i++) {
			document.getElementsByTagName('pagenumber')[i].textContent = (i+1).toString()+"/"+totalSlides.toString();
		}
	</script>
</Presentation>
