<script>
</script>

<header>
	<script
		src="https://kit.fontawesome.com/86e57103de.js"
		crossorigin="anonymous"
	></script>
	<div style="height: 0;">
		<div id="buttons" style="padding: 10px;">
		 <slot />
		</div>
	   </div>

</header>

<style>
	#buttons {
		display: flex;
		justify-content: space-between;
		color: white;
		font-size: 20px;
		z-index: 1; 
		position: absolute; 
		top: 20px;
		left: 20px;
	}
</style>
