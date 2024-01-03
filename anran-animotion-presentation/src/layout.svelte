<div>
	<topbar class="table w-full h-10% bg-[#0065BD]" style="font-size:4vh" >
		<tr > </tr>
		<tr style="color: #8AB1DA;"> </tr>
	</topbar>

	<botbar class="botbar">
		<div class="block w-[15%]"> Anran Wang </div>
		<div class="block w-[75%]"> This is your title </div>
		<div class="block w-[10%]">
			<pagenumber>
		</div>
	</botbar>

	<div class="h-full p-16 middle">
		<slideID>here is slide id</slideID>
		<script>newPage();</script>
		<slot />
		<test> test area </test>
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
