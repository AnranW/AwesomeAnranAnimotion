<script lang="ts">
	import { Presentation, Slide } from '@components'
	import Layout from './layout.svelte'
</script>

<Presentation>	
	<script>
		var currentChapterName="";
		var currentChapterNumber=0;
		var chapterNames=[];
		// data structure: [chapter number, chapter name, slideID]
		var presentationData = []; 
		function newChapter(chapterName){
			currentChapterName=chapterName; 
			currentChapterNumber++;
			chapterNames.push(chapterName);
		}
		// called when new slide is created
		var page=0; 
		function newPage(){
			page++; //note that page n has index n-1
			document.getElementsByTagName("slideID")[page-1].innerHTML=page;
			presentationData.push({chapternr: currentChapterNumber, chapter:currentChapterName,pagenr:page});
		}


	</script>
	<!-- intro -->
	<script>newChapter("Introduction")</script>

	<Slide>
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

	<Slide>
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
	<Slide>
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
	<Slide>
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
	<Slide>
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
	<Slide>
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
			for (let j = 0; j < totalChapters; j++) {
				// fill in chapter names
				document.getElementsByTagName('tr')[i*2].innerHTML += "<th>"+chapterNames[j]+"</th>" ;
				// document.getElementsByTagName("td")[i+].style.color="white";
				// fill in dots
				let slidesInChapter = presentationData.filter(item => item.chapter == chapterNames[j]);
				let begin = slidesInChapter[0].pagenr;
				let end = slidesInChapter[slidesInChapter.length-1].pagenr;
				let circles=toCircle(begin,end);
				document.getElementsByTagName('tr')[i*2+1].innerHTML += "<td>"+ circles +"</td>";
			}
			// then set corresponding circle to white
			document.getElementsByTagName("circle-"+(i+1))[i].style.color="white";
			// also the chapter names 
			let chapterNr = presentationData.filter(item => item.pagenr == i+1)[0].chapternr;
			document.getElementsByTagName("th")[(i)*totalChapters+chapterNr-1].style.color="white";
			// document.getElementsByTagName('tr')[i*2+chapterNr].style.color="white";
		}
		// circles: start, start+1, . . . , end are created
		function toCircle(begin,end){
			let circles = ""; 
			for (let i=begin; i<=end; i++){
				circles+="<circle-"+i+"> ° </circle-"+i+">";
			}
			return circles;
		}
	</script>

	<script> 
		// test area 
		document.getElementsByTagName('test')[1].innerHTML ="currentSlide";
		let currentSlide = window.location.hash.slice(2); 
		document.getElementsByTagName('test')[1].innerHTML =presentationData[5].chapternr;

	</script>
	
	
</Presentation>
