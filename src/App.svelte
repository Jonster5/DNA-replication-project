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

	let checked: boolean = false;

	const repsteps: Array<item> = [
		{
			title: 'Helicase Seperates the DNA strands',
			text:
				'An enzyme called <em>Helicase</em> separates the incoming DNA in what is called a <em>Replication Fork</em>. This forms two strands of split DNA',
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
				'<em>Primase</em> applies a small bit of <em>RNA primer</em> to the nucleotides. This is done many times on the <em>lagging strand.</em>',
			img: 'images/Primase.svg',
		},
		{
			title:
				"DNA Polymerase Adds Nucleotides to the 3' End of the Primer",
			text:
				"The enzyme <em>DNA Polymerase</em> can only add <em>nucleotides</em> in the <em>5' -> 3'</em> direction. This means the process is continous on the <em>Leading Strand</em>, but on the <em>Lagging Strand</em>, this must be done in small chunks called <em>Okazaki Fragments</em>",
			img: 'images/PolymeraseWrite.svg',
		},
		{
			title: 'DNA Polymerase Replaces the Primer and Proofreads the DNA',
			text:
				'<em>DNA Polymerase</em> then goes back and replaces all of the <em>RNA primer</em> with DNA, and checks the new DNA for any errors',
			img: 'images/PolymeraseRead.svg',
		},
		{
			title: 'Ligase Stitches it All Back Together',
			text:
				'Once the <em>DNA Polymerase</em> finished proofreading, a new enzyme called <em>Ligase</em> runs over the DNA and stiches all of the <em>Okazaki Fragments</em> into one continuous line. Now we have two identical copies of the original DNA',
			img: 'images/Ligase.svg',
		},
	];

	const terms: Array<item> = [
		{
			label: 'A',
			title: "Chargaff's Rule",
			text:
				"Chargaff's Rule states that the amount of <em>A</em> bases is always equal to the amount of <em>T</em> bases, and the amount of <em>G</em> bases is equal to the amount of <em>C</em> bases",
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
			title: "3' & 5', and Complimentary Strands",
			text:
				"Each of the strands that makes up DNA has two ends, <em>5'</em> and <em>3'</em>. All DNA flows from the <em>5'</em> end to the <em>3'</em>. <em>Complimentary DNA</em> are when two DNA strands' sequence of <em>nucleotides</em> match one another",
			img: 'images/3prime5prime.svg',
		},
		{
			label: 'D',
			title: 'Leading Strand, Lagging Strand, and Antiparallel',
			text:
				"The <em>Leading Strand</em> is the strand of DNA that after being separated by <em>helicase</em>, flows out with the <em>5'</em> end first. The <em>Lagging Strand</em> is the strand that flows <em>3'</em> end out first. This type of behavior is called <em>Antiparallel</em>",
			img: 'images/leadlaggingstrands.svg',
		},
		{
			label: 'E',
			title: 'Okazaki Fragments',
			text:
				"On the <em>lagging strand</em>, <em>DNA Polymerase</em> can't apply <em>nucleotides</em> continuously like it does on the <em>leading strand</em>, so it does it in small chunks called <em>Okazaki Fragments</em>",
			img: 'images/Okazaki.svg',
		},
		{
			label: 'F',
			title: 'Primase and RNA Primers',
			text:
				'Before <em>DNA Polymerase</em> can start laying down <em>nucleotides</em>, it needs to know where to start. The enzyme <em>Primase</em> applies a small bit of <em>complimentary</em> RNA called a <em>RNA Primer</em>, to the DNA strand so <em>DNA Polymerase</em> can bind to it',
			img: 'images/Primer.svg',
		},
		{
			label: 'G',
			title:
				'Origin of Replication, Replication Fork, and Replication Bubble',
			text:
				'The <em>Origin of Replication</em> is the point in the DNA where <em>helicase</em> creates a <em>Replication fork</em>, which is where the DNA splits into two strands. The bubble-like shape the two DNA strands create is called the <em>Replication Bubble</em>',
			img: 'images/ReplicationORR.svg',
		},
		{
			label: 'I',
			title: 'Central Dogma',
			text:
				'<em>Central Dogma</em> is the process of taking the information stored within DNA, and using it to create a functional product, such as a protein',
			img: 'images/Dogma.svg',
		},
		{
			label: 'J',
			title: 'Semiconservative',
			text:
				'DNA Replication is reffered to as a <em>Semiconservative</em> process, because after converting one line of DNA into two new ones, each of the two new lines contain half of the original',
			img: 'images/Semiconservative.svg',
		},
	];

	const repheight = 230;
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
					{checked}
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
					{checked}
				/>
			{/each}
		</section>
	</div>
	<label>
		{#if !checked}
			Show all descriptions
		{:else}
			Hide all descriptions
		{/if}
		<input type="checkbox" bind:checked />
	</label>
</main>

<style lang="scss">
	@import 'styles/mixins';
	@import 'styles/vars';

	main {
		@include container;
		// background: #01010188;
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

	label {
		position: absolute;
		top: 2vh;
		right: 2vw;
		color: white;
		font-family: 'Courier New', Courier, monospace;
	}
</style>
