<script>
    import Progressbar from "./progressbar.svelte"; 
    export let principes;
</script>

<!-- <pre>{JSON.stringify(principes, null, 2)}</pre> -->

<aside>
    <ul>
        {#each principes as principe}
        <li>
            <a href="/">
                <h5>{principe.titel}</h5>
                <span>Principe {principe.index}</span>
                <Progressbar />
            </a>
        </li>
        {/each}
    </ul>
</aside>

<style>
    h5 {
        font-size: 1.5rem;
        font-weight: 500;
        font-family: "Inter", sans-serif;
    }

    span {
        font-weight: 100;
    }

    aside {
        display: block;
        position: -webkit-sticky;
        position: sticky;
        top: 1em;
        height: 100%;
        background-color: var(--c-container);
        border-radius: 0.5em;
        border: solid 1px var(--c-container-stroke);
        flex-grow: 400;
        flex-basis: 0;
        align-self: start;
    }

    li {
        display: flex;
    }

    a {
        width: 100%;
        height: 100%;
        border-bottom: 1px solid var(--c-container-stroke);
        padding: 1em;
        color: white;
        text-decoration: none;
    }

    span {
        font-weight: 100;
    }
</style>