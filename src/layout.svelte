<!-- does not work well with browser where toolbar is not hidable -->
<div style="font-family:Arial, Helvetica, sans-serif" class="w-[100vw] h-[100vh]"> 
	<table class="topbar" >
		<tr style="border-style:hidden;vertical-align: bottom;"> <td> </td>  </tr>
		<tr style="border-style:hidden;"> <td> </td> </tr>
	</table>


	<div class="h-full middle">
		<!-- <slideID>here is slide id</slideID><br> -->
		<!-- <test> test area </test> -->
		<script>newPage();</script>
		<middle> 
			<slot />
		</middle>
	</div>

	<botbar class="botbar">
		<author class="block w-[15%]">  </author>
		<mytitle class="block w-[75%]"> </mytitle>
		<div class="block w-[10%]">
			<pagenumber>
		</div>
	</botbar>
</div>

<style>
	:root{
		--tumblue: #0065BD;
		--secondblue: #8AB1DA;
		--themecolor: var(--tumblue);
		--themecolorlight: var(--secondblue);
	}
	.topbar{
		width:100%; 
		height: 7%; 
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
		bottom: 0; 
		width: 100%; 
		height: 5%; 
		text-align: center;
		display: flex;
	}
	/* defines the body in the middle  */
	.middle{
		/* background: yellowgreen; */
		color: black;
		position: fixed; 
		top: 7%; 
		height: 88%; 
		width: 100%; 
	}
</style>
