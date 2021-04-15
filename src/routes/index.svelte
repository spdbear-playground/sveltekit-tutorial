<script context="module">
	import Client from './../../utils/client';
	import PrismicDom from 'prismic-dom';

	export async function load() {
		const document = await Client.getByUID('page', 'homepage', {});
		return {
			props: {
				document
			}
		};
	}
</script>

<script>
	export let document;
</script>

<main>
	<div class="header container" style="background-image: url('{document.data.image.url}')">
		<h1>{document.data.title}</h1>
	</div>
	<div class="container">
		<div class="text">
			{@html PrismicDom.RichText.asHtml(document.data.content)}
		</div>
	</div>
</main>

<!--  -->
<style>
	.header {
		color: white;
		background-size: cover;
		min-height: 25vw;
		padding-top: 2rem;
		justify-content: flex-end;
	}
</style>
