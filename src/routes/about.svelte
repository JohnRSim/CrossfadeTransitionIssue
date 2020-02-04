<script>
	import { onDestroy, onMount } from 'svelte';
	import { send, receive } from "crossfade";
	import { fade } from 'svelte/transition';

	let showSection = false;
	let showRelatedContent = false;
	let bgSectionTimeout;
	let showRelatedSectionTimeout;

	onMount(() => {
		//trigger back to replicate issue
		setTimeout(()=> {
			window.history.back();
		},1000);
		//show some outter content
		showSection = true;
		//add dummy timeout to display content
		showRelatedSectionTimeout = setTimeout(() => {
			//show inner content
			showRelatedContent = true;
		},1400);
	});
</script>

<style>
	h1,
	figure,
	p {
	  text-align: center;
	  margin: 0 auto;
	}

	h1 {
	  font-size: 2.8em;
	  text-transform: uppercase;
	  font-weight: 700;
	  margin: 0 0 0.5em 0;
	}

	h1 span {
	  position: relative;
	  display: inline-block;
	}
	img {
	  width: 100%;
	  max-width: 100px;
	  vertical-align: baseline;
	}

	p {
	  margin: 1em auto;
	}

	@media (min-width: 480px) {
	  h1 {
	    font-size: 4em;
	  }
	}

	.smrtr-section-wrapper {
		padding: 15px 25px 40px 25px;
		margin-top:0px;
		animation-name: example;
		animation-duration: 1s;
		animation-delay: 0.2s;
		animation-fill-mode: forwards;
		opacity:0;
	}
	@keyframes example {
		from {margin-top: 100px; opacity:0;}
		to {margin-top: 0px; opacity:1;}
	}

</style>

<main>
	<h1>
		<img out:send="{{key: 'borat'}}" in:receive="{{key: 'borat'}}" alt='Meow' src='meow.png'>
		<span out:send="{{key: 'title'}}" in:receive="{{key: 'title'}}">ABOUT PAGE</span>
	</h1>

	{#if showSection}
		<article class="smrtr-section-wrapper pageTransition" transition:fade>
			test
		</article>
		{#if (showRelatedContent)}
			<div transition:fade>
				hello World
			</div>
		{/if}
	{/if}
</main>