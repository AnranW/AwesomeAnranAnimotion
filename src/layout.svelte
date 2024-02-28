<div style="font-family:Arial, Helvetica, sans-serif">
	<table class="topbar" >
		<tr style="border-style:hidden;vertical-align: bottom;"> <td> </td>  </tr>
		<tr style="border-style:hidden;"> <td> </td> </tr>
	</table>

	<botbar class="botbar">
		<author class="block w-[15%]">  </author>
		<mytitle class="block w-[75%]"> </mytitle>
		<div class="block w-[10%]">
			<pagenumber>
		</div>
	</botbar>

	<div class="h-full middle">
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
		font-size:2vh;
		color: var(--themecolorlight);
		justify-content: center;
		align-items: center;
		/* display: flex; */
		/* flex-direction: row; */
		/* grid-template-columns: auto auto auto auto auto auto; */
	}
	/* block inside of topbar or botbar  */
	.block{
		display: flex;
		height:full; 
		justify-content: center;
		align-items: center;
		font-size: 2vh;
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
