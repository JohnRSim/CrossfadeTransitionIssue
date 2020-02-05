<script>
	import { onDestroy, onMount } from 'svelte';
	import { send, receive } from "crossfade";
	import { fade } from 'svelte/transition';

	let showSection = false;
	let dummydata = 'testdata';
	onMount(() => {
		//trigger back to replicate issue
		setTimeout(()=> {
			window.history.back();
		},1000);
		//show some outter content
		showSection = true;

		//imagine ajax request here that re-inits showsect
		setTimeout(()=> {
			dummydata = 'testdata2';
			showSection = true;
		},1400);
	});

	onDestroy(() => {
		//hide tiles
		showSection = false;
	});

</script>

<style>

.smrtr-article-wrapper {
	padding: 15px 25px;
	margin-top:0px;
	animation-name: example;
	animation-duration: 1s;
	/*animation-delay: 0.2s;*/
	animation-fill-mode: forwards;
	opacity:0;
}
@keyframes example {
  from {margin-top: 100px; opacity:0;}
  to {margin-top: 0px; opacity:1;}
}

</style>

<svelte:head>
	<title>about:: Article :: Atlas</title>
</svelte:head>

<section class="wrapper article">
	<h1>
		<span out:send="{{key: undefined}}" in:receive="{{key: undefined}}">ABOUT PAGE</span>
	</h1>

	{#if showSection}
	<article class="smrtr-article-wrapper pageTransition" in:fade="{{delay: 200}}" out:fade>
		<h1 class="article-main-title">teset</h1>
		<h2 class="article-sub-title">test</h2>

		<div class="article-introductory-paragraph">
			{dummydata}
		</div>
	</article>
	{/if}
</section>