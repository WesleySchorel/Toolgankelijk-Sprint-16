<script>
	import logo from "$lib/assets/vervoerregio_amsterdam_logo.svg";
	import informationIcon from "$lib/assets/information_icon.svg";
	import darkmodeIcon from "$lib/assets/dark_mode_icon.svg";
	import BreadCrumbs from "./bread-crumbs.svelte";

	export let params;
	export let partners;
	export let websites;
</script>

<header>
	<nav>
		<a href="/" aria-label="Ga naar het overzicht met alle partners"><img src={logo} alt="Logo van Vervoerregio Amsterdam"></a>
		<BreadCrumbs {params} {partners} {websites} />

		<div class="options">
			<a href="/info">
				<img
					class="information-icon-img"
					src={informationIcon}
					alt="information icon"
				/>
			</a>
			<a href="/info">
				<img
					class="information-icon-img"
					src={darkmodeIcon}
					alt="information icon"
				/>
			</a>
		</div>
	</nav>
</header>

<style>
	header {
		position: sticky;
		top: 0;
		display: flex;
		flex-direction: column;
	}

	nav {
		display: flex;
		align-items: center;
		gap: 1rem;
		background-color: #202020;
		padding: 1em;
		border-bottom: 2px solid #454545;
	}
	nav > a {
		z-index: 2;
	}
	.options {
		display: flex;
		align-items: center;
		gap: .8rem;
		margin-left: auto;
		z-index: 2;
	}

	@media only screen and (max-width: 990px) {
		nav {
			display: grid;
			grid-template-rows: auto;
			gap: 0.4rem;
		}
		nav > a,
		.options {
			grid-row: 1;
		}
	}
</style>
