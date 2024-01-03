<script lang="ts">
	import { Presentation, Slide } from '@components'
	import Layout from './layout.svelte'
</script>

<Presentation>	
	<script>
		var currentChapterName="";
		var chapterNames=[];
		// data structure: [chapter name, slideID]
		var presentationData = []; 
		function newChapter(chapterName){
			currentChapterName=chapterName; 
			chapterNames.push(chapterName);
		}
		// called when new slide is created
		var page=0; 
		function newPage(){
			page++; //note that page n has index n-1
			document.getElementsByTagName("slideID")[page-1].innerHTML=page;
			presentationData.push({chapter:currentChapterName,pagenr:page});
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

	<script> newChapter("To wrap it up") </script>
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
		const totalChapters = chapterNames.length;
		// show slide number with total slide number
		for (let i = 0; i < totalSlides; i++) {
			document.getElementsByTagName('pagenumber')[i].textContent = (i+1).toString()+"/"+totalSlides.toString();
			// fill in chapter names
			for (let j = 0; j < totalChapters; j++) {
				document.getElementsByTagName('tr')[i*2].innerHTML += "<td>"+chapterNames[j]+"</td>" ;
		// 	// 	// fill in dots
				// let slidesInChapter = presentationData.filter(item => item.chapter == chapterNames[j]);
				// let start = slidesInChapter[0].pagenr;
				// let end = slidesInChapter[slidesInChapter.length-1].pagenr;
				// document.getElementsByTagName('tr')[i*2+1].innerHTML += "<td>"+ toCircle(start,end) +"</td>";
			}
		}
	</script>
	
	<!-- to create one circle per slide -->
	<!-- given n, create n circles  -->
	<script>
		let circles = []; 
		// circles start, start+1, . . . , end-1 are created
		function toCircle(start,end){
			for (let i=start; i<end; i++){
				circles+="<div id=\"circle-"+i.toString()+"\"> ° </div>";
			}
			return circles;
		}
	</script>
	
	
</Presentation>
