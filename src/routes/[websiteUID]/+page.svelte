<script>
	import { Heading, Website } from 'toolgankelijk-component-library';
    import { page } from '$app/stores';

    export let data;

    $: heading = {
        titel: data.websitesData.website.titel,
        homepage: data.websitesData.website.homepage
    };

    // data voor websites component
    $: website = data.websitesData.website.urls;
    $: overzicht = data.websitesData.website;
    $: params = $page.params.websiteUID;
</script>

<!-- {JSON.stringify(data, null, 2)} -->

<Heading {heading} />

<section>
    <button>Project toevoegen</button>
    <form>
        <label for="partner-search">Zoek een website</label>
        <input
            type="search"
            id="partner-search"
            placeholder="Home"
            on:input={(e) => console.log(e)}
        />
    </form>
</section>

<section class="website-list">
    {#each website as website}
        <Website {website} {overzicht} {params} />
    {/each}
</section>

<style>
    section{
        display: flex;
        justify-content: space-between;
        margin: 0 1em;
        margin-bottom: 1em;
    }

    button{
        border-radius: 0.25em;
        padding: 0.5em 1em;
        color: var(--c-white);
        background-color: var(--c-modal-button);
        border: none;
        font-weight: 600;
        font-size: 1em;
        transition: 0.3s;
        cursor: pointer;
    }

    button:hover {
        opacity: 0.75;
    }

    /* form */
    form {
        display: flex;
        justify-content: flex-end;
        align-items: center;
        gap: 1em;
        font-weight: 600;
    }

    input {
        padding: 0.5em;
        border: 1px solid var(--c-modal-button);
        background-color: var(--c-container);
        border-radius: 0.25em;
        color: var(--c-white);
        width: 8.5em;
        font-size: 1em;
        font-weight: 600;
        padding-left: .75em;
    }
    /* form end */
    .website-list{
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(20em, 1fr));
        gap: 1em;

        list-style-type: none;
        margin: 0 1em;
    }
</style>
