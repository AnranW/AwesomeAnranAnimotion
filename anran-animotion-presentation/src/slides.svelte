<script lang="ts">
	import { Presentation, Slide } from '@components'
	import Layout from './layout.svelte'
</script>

<Presentation>	
	<script>
		// information about this presentation 
		const author = "Anran Wang"; 
		const title = "This Is My Own Title";
		const subtitle = "And here is my subtitle";
		const department = "Department of Informatics"; 
		const university = "Technical University of Munich"; 
		// the url of this presentation 
		// const myURL="http://localhost:5173/"
		var currentChapterName="";
		var currentChapterNumber=0;
		var chapterNames=[];
		var toc = false;  // whether toc is to be generated
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
			<div class="flex h-[25vh] w-[90vw] bg-[var(--themecolor)] text-white items-center justify-center gap-[100px]">
				<div>
					<div class="text-[6vh]">
						<script> document.currentScript.outerHTML=title; </script>
					</div>
					<br>
					<div class="text-[4vh]">
						<script> document.currentScript.outerHTML=subtitle; </script>
					</div>
				</div>
			</div>
			<br>
			<div> 
				<script> document.currentScript.outerHTML=author; </script>
			</div>
			<br>
			<div class="text-[3vh]"> 
				<script> document.currentScript.outerHTML=department+"<br>"+university; </script>
			</div>
			<div class="text-[3.5vh]"> 
				<br>
				<script> 
					let today = new Date(); 
					document.currentScript.outerHTML=today.toISOString().split('T')[0]; 
				</script>
			</div>
			<br>
			<div class="flex items-center justify-center">
				<img class="h-[10vh] align-middle" src="public/tum-logo.svg" alt="tum logo">
			</div>

				
		</Layout>
	</Slide>
	<!-- TOC -->
	<Slide>
		<script>toc=true;</script>
		<Layout>
			<toc class="flex h-full items-center justify-center gap-[100px]">
				<chpicons> </chpicons>
				<chpnames class="text-left"> </chpnames>
			</toc>
		</Layout>
	</Slide>
	
	<!-- intro -->
	<script>newChapter("Introduction")</script>

	<Slide>
		<Layout>
			<div class="flex h-full items-center justify-center gap-[100px]">
				chapter 1 page 1
				<div>
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
					<p>Manim</p>
				</div>

				<div>
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
					<p>Manim</p>
				</div>

				<div>
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
					<p>Manim</p>
				</div>

				<div>
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
					<p>Manim</p>
				</div>

				<div>
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
					<a href="#slide-4">  hello </a>
					<p>Manim</p>
				</div>

				<div>
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
		for (let i = 0; i < totalSlides; i++) {
			// add id to slides after the fact 
			// one section, one slide
			document.getElementsByTagName('section')[i].setAttribute("id", "slide-"+(i+1));
			// add author name 
			document.getElementsByTagName('author')[i].innerText=author;
			// add title 
			document.getElementsByTagName('title')[i].innerText=title;
		}
		// show slide number with total slide number
		for (let i = 0; i < totalSlides; i++) {
			document.getElementsByTagName('pagenumber')[i].outerHTML = "<pagenumber>"+(i+1)+"/"+totalSlides.toString();
			for (let j = 0; j < totalChapters; j++) {
				// fill in chapter names
				document.querySelectorAll("[data-name='chprow']")[i].innerHTML += "<th data-name=\"chpcol\" style=\"font-weight:normal\">"+chapterNames[j]+"</th>";
				// fill in dots
				let slidesInChapter = presentationData.filter(item => item.chapter == chapterNames[j]);
				let begin = slidesInChapter[0].pagenr;
				let end = slidesInChapter[slidesInChapter.length-1].pagenr;
				let circles=toCircle(begin,end);
				document.querySelectorAll("[data-name='dotrow']")[i].innerHTML += "<td>"+ circles +"</td>";
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
				document.querySelectorAll("[data-name='chpcol']")[(i)*(totalChapters)+chapterNr-1].style.color="white";
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
				// document.getElementsByTagName('toc')[0].innerHTML += "<tr> <td> <div >"+i+ "</div> </td> <td>"+chapterNames[i-1]+"</td> </tr> ";
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
			background: var(--themecolor);
		}
		.dot {
			height: 15px;
			width: 15px;
			background: rgba(0,0,0,0);
			border-radius: 50%;
			border: 1.5px solid var(--themecolorlight);
			display: inline-block;
		}
	</style>
</Presentation>

