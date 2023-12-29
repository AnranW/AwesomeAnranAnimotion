


<div>

	<topbar class="topbar" >
		This is the structure area.  
	</topbar>
	<botbar class="botbar">
		<script>
			document.getElementById("authorname").innerHTML = "Anran Wang"
			document.getElementById("shorttitle").innerHTML = "This is the title of your presentation."
		</script>		
		<div class="block w-[15%]"> <span id="authorname"> </div>
		<div class="block w-[75%]"> <span id="shorttitle"> </div>
		<div class="block w-[10%]">
			<span id="pagenumber"> / <span id="totalpage">
			<!-- <script>
				newPage();
				let pagenumber="pagenumber"+page.toString();
			</script> -->
		</div>
		<script>
			let page=0; 
			function newPage(){
				page++;
				document.getElementById("pagenumber").setAttribute("id","pagenumber"+page) ;
				document.getElementById("pagenumber1").innerHTML = page.toString(); 
				document.getElementById("pagenumber1").setAttribute("id","pagenumber"+page) ;
				document.getElementById("pagenumber2").setAttribute("id","pagenumber"+page) ;
			}
			newPage();
		</script>

	</botbar>

	<div class="h-full p-16 middle">
		<slot />
	</div>
</div>

<style>
	/* block inside of topbar or botbar  */
	.block{
		display: flex;
		height:full; 
		justify-content: center;
		align-items: center;
		font-size: 3vh;
	}
	/* defines the top bar  */
	.topbar {
		display: flex;
		justify-content: center;
		align-items: center;
		background-color: #0065BD;
		position: fixed; 
		left: 0%; 
		top: 0%; 
		width: 100%; 
		height: 10%; 
		font-size: 8vh;
		/* Viewport is the browser window size. 1vw = 1% of viewport width.  */
	}
	/* defines the bottom bar  */
	.botbar{
		background-color: #0065BD;
		position: fixed; 
		left: 0%; 
		bottom: 0%; 
		width: 100%; 
		height: 5%; 
		text-align: center;
		display: flex;
	}
	/* defines the body in the middle  */
	.middle{
		background: green;
		position: fixed; 
		top: 10%; 
		height: 85%; 
		width: 100%; 
	}

</style>
