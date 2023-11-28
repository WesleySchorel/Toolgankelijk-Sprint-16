<script>
	// how to make a client side javascript condition check?
	export let website;
	import { Progressbar } from '$lib/index.js';

	const faviconAPI =
		'https://t1.gstatic.com/faviconV2?client=SOCIAL&type=FAVICON&fallback_opts=TYPE,SIZE,URL&url=';
</script>

<article class="website">
	<a href={website.slug}>
		<section class="logo-partner-section">
			<img
				height="60"
				src="{faviconAPI}{website.homepage}/&size=128"
				alt="partner logo"
				loading="lazy"
			/>
			<h2 class="name">{website.titel}</h2>
		</section>

		<section class="more-info-section">
			<p>Laatst bewerkt: 12 minuten geleden</p>

			<Progressbar />
		</section>
	</a>
</article>

<style>
	article {
		display: flex;
	}

	article a {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		gap: 2.25em;
		color: var(--c-text);
		text-decoration: none;
		background-color: var(--c-container);
		padding: 1em;
		border-radius: 0.5em;
		border: solid 1px var(--c-container-stroke);
		width: 100%;
		transition: 0.25s ease;
	}

	article a:hover {
		border: solid 1px var(--c-pink);
	}

	.logo-partner-section {
		display: flex;
		align-items: flex-start;
		justify-content: space-between;
	}

	h2 {
		font-size: 1.25em;
		margin-top: 0.05em;
		margin-left: 0.5em;
	}

	p {
		font-size: 1em;
		font-weight: 400;
	}

	.more-info-section {
		display: flex;
		flex-direction: column;
		font-size: 0.9em;
	}

	:focus {
		outline: 2px solid var(--c-pink);
	}
</style>
