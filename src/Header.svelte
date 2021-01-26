<script lang="ts">
	export let heading: string;
	export let color: string;
</script>

<main>
	<h2 style={`color: ${color}`}>{heading}</h2>
</main>

<style lang="scss">
	main {
		width: 100%;

		h2 {
			font-size: 2vw;
			// color: orange;
			text-align: center;
		}
	}
</style>
