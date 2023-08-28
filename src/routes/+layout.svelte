<script>
	// import 'open-props/style';
	// import 'open-props/normalize';
	// import 'open-props/buttons';
	import 'ress/ress.css'
</script>

<!-- <svelte:head> -->
<!-- 	<link rel="stylesheet" href="%sveltekit.assets%/ress/dist/ress.min.css" /> -->
<!-- </svelte:head> -->
<slot />

<style>
	/* foldit-regular - latin */
	@font-face {
		font-display: swap; /* Check https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display for other options. */
		font-family: 'Foldit';
		font-style: normal;
		font-weight: 400;
		src: url('/fonts/foldit-v3-latin-regular.woff2') format('woff2'); /* Chrome 36+, Opera 23+, Firefox 39+, Safari 12+, iOS 10+ */
	}
	/* foldit-700 - latin */
	@font-face {
		font-display: swap; /* Check https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display for other options. */
		font-family: 'Foldit';
		font-style: normal;
		font-weight: 700;
		src: url('/fonts/foldit-v3-latin-700.woff2') format('woff2'); /* Chrome 36+, Opera 23+, Firefox 39+, Safari 12+, iOS 10+ */
	}
</style>
