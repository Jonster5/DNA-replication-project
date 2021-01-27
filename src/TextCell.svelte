<script lang="ts">
	import { fly } from 'svelte/transition';
	import { cubicOut, quintOut } from 'svelte/easing';

	export let title: string;
	export let text: string;
	export let step: number | string;
	export let side: number;
	export let height: number;
	export let img: string;

	let showImage = true;
	let showText = false;
</script>

<div
	class="c"
	style={`height: ${height}px`}
	on:click={() => {
		if (showImage && !showText) {
			showImage = false;
			setTimeout(() => (showText = true), 360);
		} else if (showText && !showImage) {
			showText = false;
			setTimeout(() => (showImage = true), 360);
		}
	}}
>
	<strong>{step}.</strong>

	{#if side === 1}
		<h3 class="t1">{title}</h3>
		{#if showImage}
			<img
				src={img}
				alt={img.split('/')[1].split('.')[0]}
				in:fly={{ y: -20, duration: 375, easing: cubicOut }}
				out:fly={{ y: -20, duration: 375, easing: cubicOut }}
			/>
		{/if}
		{#if showText}
			<p
				in:fly={{ y: 20, duration: 375, easing: cubicOut }}
				out:fly={{ y: 20, duration: 375, easing: cubicOut }}
			>
				{@html text}
			</p>
		{/if}
	{:else}
		{#if showImage}
			<img
				src={img}
				alt={img.split('/')[1].split('.')[0]}
				in:fly={{ y: -20, duration: 375, easing: cubicOut }}
				out:fly={{ y: -20, duration: 375, easing: cubicOut }}
			/>
		{/if}
		{#if showText}
			<p
				in:fly={{ y: 20, duration: 375, easing: cubicOut }}
				out:fly={{ y: 20, duration: 375, easing: cubicOut }}
			>
				{@html text}
			</p>
		{/if}
		<h3 class="t2">{title}</h3>
	{/if}
</div>

<style lang="scss">
	@import 'styles/mixins';
	@import 'styles/vars';

	.c {
		width: 100%;
		display: flex;
		margin: 1vh 0;
		transition-duration: 100ms;

		font-family: 'Lato';

		&:hover {
			background: $filterbg;
			cursor: pointer;
		}
	}

	h3 {
		margin: auto 0;
		font-size: 1.5vw;
		text-align: center;
		min-width: 30%;
		max-width: 30%;
	}

	img {
		margin: auto 2vw;
		width: 50%;
		height: auto;
		color: white;
	}

	.t1 {
		@extend h3;
		color: $subtitle1;
	}

	.t2 {
		@extend h3;
		color: $subtitle2;
	}

	strong {
		color: $step;
		margin: 2vh 3vw;
		font-size: 2vw;
	}

	p {
		color: $text;
		margin: auto auto;
		word-wrap: break-word;
		width: 50%;
		line-height: 25px;
		padding: 3vh 3vw;
	}
</style>
