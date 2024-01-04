<script lang="ts">
	import { Presentation, Slide } from '@components'
	import Layout from './layout.svelte'
</script>

<Presentation>	
	<script>
		// the url of this presentation 
		// const myURL="http://localhost:5173/"
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
			// document.getElementsByTagName("slideID")[page-1].innerHTML=page;
			presentationData.push({chapternr: currentChapterNumber, chapter:currentChapterName,pagenr:page});
		}
	</script>

	<!-- title page -->
	<Slide>
		<Layout>
			<div class="flex h-full items-center justify-center gap-[100px]">
				title page 
			</div>
		</Layout>
	</Slide>
	<!-- TOC -->
	<Slide>
		<script>var toc=true;</script>
		<Layout>
			<div class="flex h-full items-center justify-left gap-[100px]">
				<chpicons> </chpicons>
				<chpnames class="text-left"> </chpnames>
			</div>
		</Layout>
	</Slide>
	
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
	<Slide id="slide-4">
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
					<a href="#slide-4">  hello </a>
					<p>Manim</p>
				</div>

				<div>
					<img width="400" src="motion-canvas.svg" alt="logo" />
					<p>Motion Canvas</p>
				</div>
			</div>
		<test> test area </test>
		</Layout>
	</Slide>
	<script>
		document.getElementsByClassName('Slide')[2].setAttribute("id", "slide-3");
	</script>
	<!-- to mimic the latex template  -->
	<script>
		const totalSlides = document.getElementsByTagName('pagenumber').length;
		const totalChapters = chapterNames.length;
		// add id to slides after the fact 
		for (let i = 0; i < totalSlides; i++) {
			// one section, one slide
			document.getElementsByTagName('section')[i].setAttribute("id", "slide-"+(i+1));
		}
		// show slide number with total slide number
		for (let i = 0; i < totalSlides; i++) {
			document.getElementsByTagName('pagenumber')[i].outerHTML = "<pagenumber>"+(i+1)+"/"+totalSlides.toString();
			for (let j = 0; j < totalChapters; j++) {
				// fill in chapter names
				document.getElementsByTagName('tr')[i*2].innerHTML += "<th style=\"font-weight:normal\">"+chapterNames[j]+"</th>" ;
				// fill in dots
				let slidesInChapter = presentationData.filter(item => item.chapter == chapterNames[j]);
				let begin = slidesInChapter[0].pagenr;
				let end = slidesInChapter[slidesInChapter.length-1].pagenr;
				let circles=toCircle(begin,end);
				document.getElementsByTagName('tr')[i*2+1].innerHTML += "<td>"+ circles +"</td>";
			}
			// first, find out if title page and toc exist 
			let chapter0 = presentationData.filter(item => item.chapternr == 0).length;
			if (i>=chapter0){
				// then set corresponding circle to white
				let circle = document.getElementsByTagName("circle-"+(i+1))[i]; 
				circle.style.background="white";
				circle.style.border="0px";
				// also the chapter names 
				let chapterNr = presentationData.filter(item => item.pagenr == i+1)[0].chapternr;
				document.getElementsByTagName("th")[(i)*(totalChapters)+chapterNr-1].style.color="white";
			}
		}
		// circles: start, start+1, . . . , end are created
		function toCircle(begin,end){
			let circles = ""; 
			for (let i=begin; i<=end; i++){
				circles+="<a href=\"#slide-" +i+ "\"><circle-" +i+ " class=\"dot\"> </circle-" +i+ "> </a>" ;
			}
			return circles;
		}

		// to create table of contents
		if (toc) {
			for (i=1; i<=chapterNames.length;i++){
			document.getElementsByTagName('chpicons')[0].innerHTML += "<div class=\"chpicon\">"+i+"</div> <br>";
			document.getElementsByTagName('chpnames')[0].innerHTML += "<div>"+chapterNames[i-1]+"</div> <br>";
			}
		}
	</script>

	<script> 
		// test area 
		let chpicons = document.getElementsByTagName('chpnames');
		document.getElementsByTagName('test')[0].innerHTML =chpicons.length;

	</script>

	<style>
		.chpicon{
			color: white;
			width:180%;
			background: #0065BD;
		}
		.dot {
			height: 15px;
			width: 15px;
			background: rgba(0,0,0,0);
			border-radius: 50%;
			border: 1.5px solid #8AB1DA;
			display: inline-block;
		}
	</style>
</Presentation>

