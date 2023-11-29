<script>
	import { Heading, Toolboard } from 'toolgankelijk-component-library';
	export let data;

	$: heading = {
		titel: data.websitesData.website.titel,
		homepage: data.urlData.url.url,
		url: data.urlData.url.slug
	};

	$: url = data.toolboardData.url;
	$: principe = data.toolboardData.principe;
	$: principes = data.toolboardData.principes;
</script>

<Heading {heading} />
<Toolboard {url} {principe} {principes} />
