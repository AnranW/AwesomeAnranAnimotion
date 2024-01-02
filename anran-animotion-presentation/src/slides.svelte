<script lang="ts">
	import { Presentation, Slide } from '@components'
	import Layout from './layout.svelte'
</script>

<Presentation>	
	<script>
		let chapter=0;
		let chapterNames = []; 
		function newChapter(name){
			chapter++;
			chapterNames+=name; 
		}
	</script>
	<!-- intro -->
	<script>newChapter("Introduction")</script>
	<Slide >
		<Layout>
			<div class="flex h-full items-center justify-center gap-[100px]">
				chapter 1 page 1
				<div>
					<img width="400" src="manim.svg" alt="logo" />
					<p id="m">Manim</p>
				</div>
			</div>
		</Layout>
	</Slide>

	<Slide animate>
		<Layout>
			<div class="flex h-full items-center justify-center gap-[100px]">
				chapter 1 page 2
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

	<script>newChapter("The actual body of this presentation")</script>
	<Slide animate>
		<Layout>
			<div class="flex h-full items-center justify-center gap-[100px]">
				chapter 2 page 1 °
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

	<script>newChapter("To wrap it up")</script>
	<Slide animate>
		<Layout>
			<div class="flex h-full items-center justify-center gap-[100px]">
				chapter 3 page 1
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
	<!-- to create one circle per slide -->
	<!-- given n, create n circles  -->
	<script>
		let circles = []; 
		function toCircle(n){
			for (let i=0; i<n; i++){
				circles+="°"
			}
		}
	</script>
	<!-- fill out chapter names into top bar -->
	<script>
		for (name in chapterNames){
			document.getElementsByTagName('structure')[0].innerHTML = <div> name </div>;
		}
	</script>
	
</Presentation>
