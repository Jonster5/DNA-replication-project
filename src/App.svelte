<script lang="ts">
	import Header from './Header.svelte';
	import TextCell from './TextCell.svelte';
	import Title from './Title.svelte';

	interface item {
		label?: string;
		title: string;
		text: string;
		img: string;
	}

	const title = 'DNA Replication';

	const repsteps: Array<item> = [
		{
			title: 'Helicase Seperates the DNA strands',
			text:
				'The first step in DNA replication is to seperate the strands of DNA. An enzyme called <em>Helicase</em> takes care of that.',
			img: 'images/Helicase.svg',
		},
		{
			title: 'Topoisomerase Prevents Supercoiling',
			text:
				'DNA naturally is coiled around itself, which can get in the way when replicating. So <em>Topoisomerase</em> unwinds the DNA and prevents it from supercoiling',
			img: 'images/Topoisomerase.svg',
		},
		{
			title: 'SSBPs Are Attached to Each Nucleotide',
			text:
				'After being split by helicase, <em>SSBPs</em> must applied to each nucleotide in order to prevent them from reform <em>hydrogen bonds</em>',
			img: 'images/SSBP.svg',
		},
		{
			title: 'Primase Applies RNA Primer to the DNA Strands',
			text:
				'<em>Primase</em> applies a small bit of RNA <em>primer</em> to the nucleotides. This is done many times on the <em>lagging strand.</em>',
			img: 'images/Primase.svg',
		},
		{
			title:
				"DNA Polymerase Adds Nucleotides to the 3' End of the Primer",
			text:
				"The enzyme <em>DNA Polymerase</em> can only add <em>nucleotides</em> in the <em>5' -> 3'</em> direction. This means the process is continous on the <em>Leading Strand</em>, but on the <em>Lagging Strand</em>, this must be done in small chunks called <em>Okazaki Fragments</em>",
			img: 'images/PolymeraseWrite.svg',
		},
	];

	const repheight = 230;

	const terms: Array<item> = [
		{
			label: 'A',
			title: "Chargaff's Rule",
			text:
				"Chargaff's Rule states that the amount of <em>A</em> bases is always equal to the amount of <em>T</em> bases, and the amount of <em>G</em> bases is equal to the amount of <em>C</em> bases.",
			img: 'images/Chargaff.svg',
		},
		{
			label: 'B',
			title: 'Nucleotides',
			text:
				'<em>Nucleotides</em> are what makes up DNA and RNA. Each Nucleotide is made up of three parts: A <em>Phosphate group</em>, a <em>Sugar</em>, and a <em>Nitrogenous base</em>',
			img: 'images/Nucleotide.svg',
		},
		{
			label: 'C',
			title: "3' and 5'",
			text:
				"Each of the strands that makes up DNA has two ends, <em>5'</em> and <em>3'</em>. All DNA flows from the <em>5'</em> end to the <em>3'</em>.",
			img: 'images/3prime5prime.svg',
		},
		{
			label: 'D',
			title: 'Leading and Lagging Strands',
			text:
				"The <em>Leading Strand</em> is the strand of DNA that after being separated by <em>helicase</em>, flows out with the <em>5'</em> end first. The <em>Lagging Strand</em> is the strand that flows <em>3'</em> end out first ",
			img: 'images/leadlaggingstrands.svg',
		},
	];

	const termheight = 230;
</script>

<svelte:head>
	<meta name="description" content="DNA Replication stuff" />
	<title>DNA Replication</title>
</svelte:head>

<main>
	<Title text={title} />
	<div>
		<section>
			<Header heading={'Steps of Replications'} color="#7154ff" />
			{#each repsteps as { title, text, img }, i}
				<TextCell
					{title}
					{text}
					side={(i + 1) % 2}
					step={i + 1}
					height={repheight}
					{img}
				/>
			{/each}
		</section>
		<section>
			<Header heading={'Other terms'} color="#54ffac" />

			{#each terms as { label, title, text, img }, i}
				<TextCell
					{title}
					{text}
					side={(i + 1) % 2}
					step={label}
					height={termheight}
					{img}
				/>
			{/each}
		</section>
	</div>
</main>

<style lang="scss">
	@import 'styles/mixins';
	@import 'styles/vars';

	main {
		@include container;
		background: #01010111;
	}

	div {
		display: flex;
		margin: auto;
		justify-content: center;
	}

	section {
		width: 45%;
		display: flex;
		flex-direction: column;
	}
</style>
