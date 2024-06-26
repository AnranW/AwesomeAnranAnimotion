<script lang="ts">
	import { Presentation, Slide, Notes } from '@components'
	import Layout from './layout.svelte'
</script>

<!-- Typical Errors
	
	"Uncaught TypeError: slidesInChapter[0] is undefined" and layout elements missing.
	→ This can happen if a chapter is defined but has no slides.

-->

<Presentation>	
	<script>
		// information about this presentation 
		const author = "Anran Wang, Christian Schuler"; 
		const authorshort = "Wang, Schuler"; 
		const title = "This Is My Own Title";
		const subtitle = "And here is my subtitle";
		const department = "Department of Informatics"; 
		const university = "Technical University of Munich"; 
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
			presentationData.push({chapternr: currentChapterNumber, chapter:currentChapterName,pagenr:page});
		}
	</script>

	<!-- title page -->
	<Slide><Layout>
		<div class="m-16 flex h-[25%] w-[90%] bg-[var(--themecolor)] text-white items-center justify-center gap-[100px]">
			<div>
				<div class="text-[6vh]">
					<span id="mytitle"> </span>
				</div>
				<br>
				<div class="text-[4vh]">
					<span id="mysubtitle"> </span>
				</div>
			</div>
		</div>
		<br>
		<div> 
			<span id="myname"></span>
		</div>
		<br>
		<div class="text-[3vh]"> 
			<span id="myuni"></span>
		</div>
		<div class="text-[3.5vh]"> 
			<br>
			<span id="mydate"></span>
		</div>
		<br>
		<figure class="w-full h-[20%]">
			<img class="align-middle" src="title-logo.svg" alt="tum logo">
		</figure>
		<!-- fill in the data for this presentation  -->
		<script> 
			document.getElementById("mytitle").innerHTML=title;
			document.getElementById("mysubtitle").innerHTML=subtitle;
			document.getElementById("myname").innerHTML=author;
			document.getElementById("myuni").innerHTML=department+"<br>"+university;
			let today = new Date(); 
			document.getElementById("mydate").innerHTML=today.toISOString().split('T')[0]; 
		</script>
	</Layout></Slide>
	<!-- TOC -->
	<Slide>
		<script>
			toc=true; // decides whether to generate table of content page
		</script>
		<Layout>
			<toc class="flex h-full items-center justify-center gap-[100px]">
				<chpicons> </chpicons>
				<chpnames class="text-left"> </chpnames>
			</toc>
		</Layout>
	</Slide>
	
	<!-- intro -->
	<script>newChapter("Introduction")</script>
	<Slide><Layout>
		<titlebar > On how to use these Presentation Slides  </titlebar>
		<ul class="a">
			<li>Press F to enter full screen.</li>
			<ul class="b"> 
				<li>To better check the layout.</li>
			</ul>
			<br>
			<li>Press fn+s to enter presenter mode.</li>
			<ul class="b"> 
				<li>Where you can see the next slide.</li>
				<li>And read your notes for each slide.</li>
			</ul>
		</ul>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<script>newChapter("Text");</script>
	<Slide><Layout>
		<titlebar > Simple Text </titlebar>
		<div class="flex h-full items-center justify-center gap-[100px]">
			You can add text, and different media files such as<br> 
			images, pdfs, videos to your presentation slides.<br>
			The following slides showcase some of these applications<br> 
			for easy reproduction.
		</div>
	</Layout></Slide>

	<Slide><Layout>
		<titlebar > A List of Text Items </titlebar>
		<ul class="a" >
			<li>The First Text Item.</li>
			<ul class="b"> 
				<li>The 1. Sub-Item.</li>
			</ul>
			<br>
			<li>The Second Text Item.</li>
			<ul class="b"> 
				<li>The 2. Sub-Item.</li>
				<ul class="c"> 
					<li>Sub-Sub-Item a.</li>
					<li>Sub-Sub-Item b.</li>
				</ul>
				<li>The 3. Sub-Item.</li>
			</ul>
			<br>
			<li>The Third Text Item.</li>
			<ul class="b"> 
				<li>The 4. Sub-Item.</li>
			</ul>
		</ul>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<script> newChapter("Images"); </script>
	<Slide><Layout>
		<titlebar > An Image with a Caption </titlebar>
		<figure>
			<img src="title-logo.svg" alt="tumlogo" class="mx-auto ">
			<figcaption> This is an example figure with caption. </figcaption>
		</figure>
	</Layout></Slide>

	<Slide><Layout>
		<titlebar > Here is a grid of images </titlebar>
		<div class="grid mt-[10%] mx-[10%]" style="grid-template-columns: auto auto auto;">
			<img src="title-logo.svg" alt="tumlogo" class="h-[40%] px-[5%]">
			<img src="title-logo.svg" alt="tumlogo" class="h-[40%] px-[5%]">
			<img src="title-logo.svg" alt="tumlogo" class="h-[40%] px-[5%]">
			<img src="title-logo.svg" alt="tumlogo" class="h-[40%] px-[5%]">
			<img src="title-logo.svg" alt="tumlogo" class="h-[40%] px-[5%]">
			<img src="title-logo.svg" alt="tumlogo" class="h-[40%] px-[5%]">
		</div>
	</Layout></Slide>

	<script> newChapter("PDFs"); </script>
	<Slide><Layout>
		<titlebar > Another PDF File as part of the Slide Deck </titlebar>
					
		<div class="h-[75%] w-[90%] mx-auto my-auto">
			<iframe src="media-sample.pdf#page=1&zoom=100" frameBorder="0" scrolling="auto" height="100%" width="100%" title="ESSV Publication"></iframe>
		</div>
		
	</Layout></Slide>

	<script> newChapter("Videos"); </script>
	<Slide><Layout>
		<titlebar > Single Animated gif File (no sound) </titlebar>
		
		<figure>
			<img src="https://i.pinimg.com/originals/d3/71/7b/d3717b91b409a8eb25a4275b30d6981a.gif" alt="this slowpoke moves" class="w-[75%] h-[75%] mx-auto my-auto p-2" />
			<figcaption> Stock-Gif of a Slowpoke for testing gif-display.<br> </figcaption>
		</figure>
		
	</Layout></Slide>
	
	<Slide><Layout>
		<titlebar > Single Video with multiple available Captions </titlebar>
			
			<figure>
				<video controls class="w-[70%] mx-auto my-auto p-2">
					<source src="media-never_gonna_give_you_up-video_medium-43_51.mp4" type="video/mp4" />
					<track kind="captions" label="English" srclang="eng" src="media-video-captions-eng.vtt"/>
					<track kind="captions" label="German" srclang="deu" src="media-video-captions-deu.vtt"/>
					<track kind="captions" label="Chinese" srclang="zho" src="media-video-captions-zho.vtt" default/>
					<track kind="captions" label="Chinese Pinyin" srclang="zho" src="media-video-captions-zhopinyin.vtt"/>
				</video>
				<figcaption> Play a video file from the repository.<br> </figcaption>
			</figure>
			
	</Layout></Slide>

	<Slide><Layout>
		<titlebar > Multiple Videos on the same Slide </titlebar>
		<div class="grid" style="grid-template-columns: auto auto;">

		<figure class="w-[100%]">
			<video controls class="mx-auto my-auto p-2" loop>
				<source src="media-never_gonna_give_you_up-video_medium-43_51.mp4" type="video/mp4" />
				<track kind="captions" label="English" srclang="eng" src="media-video-captions-eng.vtt"/>
				<track kind="captions" label="German" srclang="deu" src="media-video-captions-deu.vtt"/>
				<track kind="captions" label="Chinese" srclang="zho" src="media-video-captions-zho.vtt" default/>
				<track kind="captions" label="Chinese Pinyin" srclang="zho" src="media-video-captions-zhopinyin.vtt"/>
			</video>
			<figcaption> Video that loops.<br>Default caption: Chinese. </figcaption>
		</figure>

		<figure class="w-[100%]">
			<video controls class=" mx-auto my-auto p-2">
				<source src="media-never_gonna_give_you_up-video_medium-43_51.mp4" type="video/mp4" />
				<track kind="captions" label="English" srclang="eng" src="media-video-captions-eng.vtt" default/>
				<track kind="captions" label="German" srclang="deu" src="media-video-captions-deu.vtt"/>
				<track kind="captions" label="Chinese" srclang="zho" src="media-video-captions-zho.vtt"/>
				<track kind="captions" label="Chinese Pinyin" srclang="zho" src="media-video-captions-zhopinyin.vtt"/>
			</video>
			<figcaption> Video without looping.<br>Default caption: English. </figcaption>
		</figure>
	</div>
		
	</Layout></Slide>

	<Slide><Layout>
		<titlebar > Multiple Videos in a Grid </titlebar>
		<div class="grid mx-auto my-auto" style="grid-template-columns: auto auto;">
			<figure>
				<video controls loop>
					<source src="media-never_gonna_give_you_up-video_medium-00_06.mp4" type="video/mp4" />
					<track kind="captions" label="English" srclang="eng" src="media-video-captions-eng.vtt" default/>
					<track kind="captions" label="German" srclang="deu" src="media-video-captions-deu.vtt"/>
					<track kind="captions" label="Chinese" srclang="zho" src="media-video-captions-zho.vtt"/>
					<track kind="captions" label="Chinese Pinyin" srclang="zho" src="media-video-captions-zhopinyin.vtt"/>
				</video>
				<figcaption class="text-[2vh]"> Video with default caption: English. </figcaption>
			</figure>

			<figure>
				<video controls loop>
					<source src="media-never_gonna_give_you_up-video_medium-06_12.mp4" type="video/mp4" />
					<track kind="captions" label="English" srclang="eng" src="media-video-captions-eng.vtt"/>
					<track kind="captions" label="German" srclang="deu" src="media-video-captions-deu.vtt" default/>
					<track kind="captions" label="Chinese" srclang="zho" src="media-video-captions-zho.vtt"/>
					<track kind="captions" label="Chinese Pinyin" srclang="zho" src="media-video-captions-zhopinyin.vtt"/>
				</video>
				<figcaption class="text-[2vh]"> Video with default caption: German. </figcaption>
			</figure>

			<figure>
				<video controls loop>
					<source src="media-never_gonna_give_you_up-video_medium-12_18.mp4" type="video/mp4" />
					<track kind="captions" label="English" srclang="eng" src="media-video-captions-eng.vtt"/>
					<track kind="captions" label="German" srclang="deu" src="media-video-captions-deu.vtt"/>
					<track kind="captions" label="Chinese" srclang="zho" src="media-video-captions-zho.vtt" default/>
					<track kind="captions" label="Chinese Pinyin" srclang="zho" src="media-video-captions-zhopinyin.vtt"/>
				</video>
				<figcaption class="text-[2vh]"> Video with default caption: Chinese. </figcaption>
			</figure>

			<figure>
				<video controls loop>
					<source src="media-never_gonna_give_you_up-video_medium-18_24.mp4" type="video/mp4" />
					<track kind="captions" label="English" srclang="eng" src="media-video-captions-eng.vtt"/>
					<track kind="captions" label="German" srclang="deu" src="media-video-captions-deu.vtt"/>
					<track kind="captions" label="Chinese" srclang="zho" src="media-video-captions-zho.vtt"/>
					<track kind="captions" label="Chinese Pinyin" srclang="zho" src="media-video-captions-zhopinyin.vtt" default/>
				</video>
				<figcaption class="text-[2vh]"> Video with default caption: Chinese Pinyin. </figcaption>
			</figure>
		</div>
		
	</Layout></Slide>

	<script> newChapter("To wrap it up"); </script>
	<Slide><Layout>
		<titlebar > Here is the title for this slide </titlebar>
		<div class="flex h-[100%] items-center justify-center">
			This template is still work on progress. 
		</div>
	</Layout></Slide>


	<!-- to mimic the latex template  -->
	<script>
		const totalSlides = document.getElementsByTagName('pagenumber').length;
		const totalChapters = chapterNames.length;
		var temp; 
		for (let i = 0; i < totalSlides; i++) {
			// one section, one slide
			document.getElementsByTagName('section')[i].setAttribute("id", "slide-"+(i+1));
			// add author name 
			document.getElementsByTagName('author')[i].innerText=authorshort;
			// add title 
			document.getElementsByTagName('mytitle')[i].innerHTML="<a href=\"#slide-1\">"+title+"</a>";
			// show slide number with total slide number
			document.getElementsByTagName("pagenumber")[i].innerHTML = (i+1)+"/"+totalSlides;
		}
		for (let i = 0; i < totalSlides; i++) {
			for (let j = 0; j < totalChapters; j++) {
				// fill in chapter names
				temp = document.querySelectorAll("table.topbar")[i]; 
				temp.getElementsByTagName("tr")[0].innerHTML += "<th data-chpcol=\"chpcol\" style=\"font-weight:normal\">"+chapterNames[j]+"</th>";
				// document.getElementsByTagName("test")[0].innerHTML="here!"; 
				// fill in dots
				let slidesInChapter = presentationData.filter(item => item.chapter == chapterNames[j]);
				let begin = slidesInChapter[0].pagenr;
				let end = slidesInChapter[slidesInChapter.length-1].pagenr;
				let circles=toCircle(begin,end);
				temp.getElementsByTagName("tr")[1].innerHTML += "<td>"+ circles +"</td>";
			}
		}
		for (let i = 0; i < totalSlides; i++) {
			// first, find out if title page and toc exist 
			let chapter0 = presentationData.filter(item => item.chapternr == 0).length;
			if (i>=chapter0){
				// then set corresponding circle to white
				let circle = document.getElementsByTagName("circle-"+(i+1))[i]; 
				circle.style.background="white";
				circle.style.border="0px";
				// also the chapter names 
				let chapterNr = presentationData.filter(item => item.pagenr == i+1)[0].chapternr;
				temp = document.getElementsByTagName("th")[(i)*(totalChapters)+chapterNr-1];
				if (temp.hasAttribute("data-chpcol")){ 
					temp.style.color="white";
				}
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
		ul.a {
			list-style-type: square;
			padding:5%;
		}
		ul.b {
			list-style-type: circle;
			margin-left:5%;
			padding:1%;
		}
		ul.c {
			list-style-type: disc;
			margin-left:10%;
			padding:1%;
		}
		ul{
			text-align: left;
			margin-left:20%;
			margin-right:5%;
			padding:1%;
		}
		titlebar{
			display: flex;
			background: rgb(242,242,242); 
			width: 100%; 
			height: 9%; 
			text-align: left;
			padding-left: 5%; 
			margin-bottom: 1%;
			align-items: center; 
			font-size: 5vh;
		}
		figure {
			border: 0px #cccccc solid;
			padding: 4px;
			margin: auto;
			height: 75%;
			width: 75%;
		}
		img{
			height:100%;
			margin:auto;
		}
		video{
			height: 100%;
			margin: auto;
		}
		figcaption {
			background-color: rgb(242,242,242);
			color: black;
			font-style: italic;
			margin: 1%;
			padding: 1%;
			text-align: center;
			font-size:3vh;
		}
	</style>
</Presentation>
