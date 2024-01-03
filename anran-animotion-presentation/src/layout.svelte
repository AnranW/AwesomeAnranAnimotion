<div>
	<topbar class="topbar table " >
		<tr style="color: #8AB1DA;"> </tr>
		<tr style="color: #8AB1DA;">  </tr>
	</topbar>

	<botbar class="botbar">
		<div class="block w-[15%]"> Anran Wang </div>
		<div class="block w-[75%]"> This is your title </div>
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
	.topbar{
		margin-top: 0.5vh;
		width:100%; 
		height: 7vh; 
		background: #0065BD; 
		font-size:3vh;
	}
	/* block inside of topbar or botbar  */
	.block{
		display: flex;
		height:full; 
		justify-content: center;
		align-items: center;
		font-size: 3vh;
	}
	/* defines the bottom bar  */
	.botbar{
		background-color: #0065BD;
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
		background: yellowgreen;
		position: fixed; 
		top: 7vh; 
		height: 88vh; 
		width: 100%; 
	}
</style>
