<div style="font-family:Arial, Helvetica, sans-serif">
	<topbar class="topbar table " >
		<tr data-name="chprow" style="color: var(--themecolorlight); vertical-align: bottom;"> </tr>
		<tr data-name="dotrow" style="color: var(--themecolorlight);">  </tr>
	</topbar>

	<botbar class="botbar">
		<author class="block w-[15%]">  </author>
		<title class="block w-[75%]"> </title>
		<div class="block w-[10%]">
			<pagenumber>
		</div>
	</botbar>

	<div class="h-full p-16 middle">
		<!-- <slideID>here is slide id</slideID><br> -->
		<!-- <test> test area </test> -->
		<script>newPage();</script>
		<slot />
	</div>
</div>

<style>
	:root{
		--tumblue: #0065BD;
		--secondblue: #8AB1DA;
		--themecolor: var(--tumblue);
		--themecolorlight: var(--secondblue);
	}
	.topbar{
		/* margin-top: 0.5vh; */
		width:100%; 
		height: 7vh; 
		background: var(--themecolor); 
		font-size:2.5vh;
	}
	/* block inside of topbar or botbar  */
	.block{
		display: flex;
		height:full; 
		justify-content: center;
		align-items: center;
		font-size: 2.5vh;
	}
	/* defines the bottom bar  */
	.botbar{
		background-color: var(--themecolor); 
		position: fixed; 
		left: 0%; 
		top: 95vh; 
		width: 100%; 
		height: 5vh; 
		text-align: center;
		display: flex;
	}
	/* defines the body in the middle  */
	.middle{
		/* background: yellowgreen; */
		color: black;
		position: fixed; 
		top: 7vh; 
		height: 88vh; 
		width: 100%; 
	}
</style>
