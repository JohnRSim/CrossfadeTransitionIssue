<script>
	import { onDestroy, onMount } from 'svelte';
	import { send, receive } from "crossfade";
	import { fade } from 'svelte/transition';

	let showIndex = false;
	let showIndexContent = false;
	let relatedContentItems = [1,2,3,4];

	onMount(() => {
		//show some outter content
		showIndex = true;
		showIndexContent = true;
	});
</script>

<style>
	.smrtr-index-wrapper {
		padding: 15px 25px 40px 25px;
		margin-top:0px;
		animation-name: example;
		animation-duration: 1s;
		animation-fill-mode: forwards;
		opacity:0;
	}
	@keyframes example {
		from {margin-top: 100px; opacity:0;}
		to {margin-top: 0px; opacity:1;}
	}
</style>
<svelte:head>
	<title>index:: Article :: Atlas</title>
</svelte:head>

<section class="wrapper section">
	<h1>
	<span out:send="{{key: undefined}}" in:receive="{{key: undefined}}">INDEX PAGE</span>
	</h1>

	{#if showIndex}
		<article class="smrtr-index-wrapper pageTransition" in:fade="{{delay: 200}}" out:fade>
			index
		</article>
		{#if (showIndexContent)}
			<div in:fade="{{delay: 1400}}" out:fade>
			{#each relatedContentItems as item, i}
				hello World
			{/each}
			</div>
		{/if}
	{/if}
</section>