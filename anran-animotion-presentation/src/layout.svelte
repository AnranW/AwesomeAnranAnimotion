<script lang="ts">
	let layout = false
</script>

<div class="relative overflow-hidden" class:layout>
	<topbar class="topbar themecolor">
		hello 
	</topbar>
	<botbar class="botbar themecolor">
		<div class="flex h-full w-30% bg-red-300">
			yoyo
		</div>
	</botbar>

	<div class="h-full p-16 middle themecolor">
		<slot />
	</div>
</div>

<style>
	.themecolor{
		background-color: #0065BD;
	}
	/* defines the top bar  */
	.topbar {
		position: fixed; 
		left: 0%; 
		top: 0%; 
		width: 100%; 
		height: 10%; 
	}
	/* defines the bottom bar  */
	.botbar{
		position: fixed; 
		left: 0%; 
		bottom: 0%; 
		width: 100%; 
		height: 5%; 
	}
	/* defines the body in the middle  */
	.middle{
		background: green;
		position: fixed; 
		top: 10%; 
		height: 85%; 
		width: 100%; 
	}
	.layout {
		outline: 4px solid aqua;
		outline-offset: -6px;
	}
</style>
