<div>
	<script>
		let page=0; 
		function newPage(){
			document.getElementsByTagName('pagenumber')[page].innerHTML = (page+1).toString();
			page++;
		}
	</script>

	<topbar class="topbar" >
		This is the structure area.  
	</topbar>
	<botbar class="botbar">
		<div class="block w-[15%]"> Anran Wang </div>
		<div class="block w-[75%]"> This is your title </div>
		<div class="block w-[10%]">
			<pagenumber>
		</div>
	</botbar>

	<div class="h-full p-16 middle">
		<script>newPage();</script>
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
		background: yellowgreen;
		position: fixed; 
		top: 10%; 
		height: 85%; 
		width: 100%; 
	}
</style>
