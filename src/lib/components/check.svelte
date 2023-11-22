<script>
    import { onMount } from 'svelte';
  
    export let principe;
    export let url;
  
    const checkedSuccescriteria = url.checks[0] ? url.checks[0].succescriteria : [];
  
    onMount(() => {
      const detailsElements = document.querySelectorAll('details');
  
      detailsElements.forEach((details) => {
        details.addEventListener('toggle', (event) => {
          if (event.target.open) {
            closeOtherDetails(details);
            scrollToDetails(details);
          }
        });
      });
    });
  
    function closeOtherDetails(currentDetails) {
      const detailsElements = document.querySelectorAll('details');
  
      detailsElements.forEach((details) => {
        if (details !== currentDetails && details.open) {
          details.open = false;
        }
      });
    }
  
    function scrollToDetails(details) {
      details.scrollIntoView({ behavior: 'smooth' });
    }
  </script>

<section>
    <form action="">
        <!-- For each loop voor alle verschillende richtlijnen -->
        {#each principe.richtlijnen as richtlijn}
        <article>
            <div>
                <span>Richtlijn {richtlijn.index}</span>
                <h3>{richtlijn.titel}</h3>
            </div>
            <!-- For each loop voor alle succescriteria in de richtlijnen -->
            {#each richtlijn.succescriteria as succescriterium}
            <details>
                <summary>
                    <label>
                        <div>
                            <span
                                >Criteria {succescriterium.index}
                                ({succescriterium.niveau})</span
                            >
                            <h4>{succescriterium.titel}</h4>
                        </div>
                        <input type="checkbox"
                        checked={checkedSuccescriteria.find((e) => e.id ===
                        succescriterium.id)} />
                    </label>
                </summary>
                <div>{@html richtlijn.uitleg.html}</div>
            </details>
            {/each}
        </article>
        {/each}
    </form>
</section>

<style>
    section {
        flex-basis: 0;
        flex-grow: 999;
    }

    form article:not(:first-child) {
        margin-top: 1em;
    }

    form article {
        background-color: var(--c-container);
        border-radius: 0.5em;
        border: solid 1px var(--c-container-stroke);
    }

    article > div {
        padding: 1em 1em 0 1em;
    }

    h3,
    h4 {
        font-size: 1.5em;
    }

    span {
        font-weight: 100;
        font-family: 1em;
    }

    label {
        width: 100%;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    label div {
        margin-left: 1em;
    }

    /* Accordion styling + custom arrow */

    details {
        padding: 1em;
    }

    section details:not(:nth-child(2)) {
        border-top: 1px solid var(--c-container-stroke);
    }

    summary {
        display: flex;
        flex-direction: row;
        align-items: center;
    }

    summary::-webkit-details-marker {
        display: none;
    }

    summary:before {
        content: "🡒";
        font-size: 1.5em;
        color: #fff;
        width: 30px;
    }

    details[open] summary:before {
        content: "🡓";
        color: var(--c-pink);
    }

    details > div {
        font-size: 0.9em !important;
        padding-top: 1em;
    }

    /* Custom checkbox styling */
    input[type="checkbox"] {
        -webkit-appearance: none;
        appearance: none;
        margin: 0;
        color: var(--c-pink);
        min-width: 2em;
        width: 2em;
        height: 2em;
        border: 0.15em solid currentColor;
        border-radius: 0.3em;
        transform: translateY(-0.075em);
        display: grid;
        place-content: center;
    }

    input[type="checkbox"]::before {
        content: "";
        width: 1em;
        height: 1em;
        clip-path: polygon(14% 44%, 0 65%, 50% 100%, 100% 16%, 80% 0%, 43% 62%);
        transform: scale(0);
        background-color: white;
    }

    input[type="checkbox"]:checked::before {
        transform: scale(1);
    }

    input[type="checkbox"]:checked {
        background-color: var(--c-pink);
    }
</style>