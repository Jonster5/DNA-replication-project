<script lang="ts">
	export let text: string;
</script>

<h1>{text}</h1>

<style lang="scss">
	@import 'styles/mixins';
	@import 'styles/vars';

	h1 {
		margin: 6vh 5vw;
		color: $title;
		font-size: 4vw;
		text-align: center;
	}
</style>
