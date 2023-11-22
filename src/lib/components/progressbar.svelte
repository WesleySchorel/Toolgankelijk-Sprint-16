<div>
	<progress id="progress-partner" max="100" value="35" />
    <label for="progress-partner">8/25</label>
</div>

<style>
    div {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: flex-end;
        gap: 1em;
        margin-top: 0.25em;
    }

    progress {
        width: 100%;
    }

    progress[value] {
        /* Reset the default appearance */
        -webkit-appearance: none;
        appearance: none;
        height: 10px;
    }

    /* chrome/safari */
    progress[value]::-webkit-progress-bar {
        background-color: var(--c-container-stroke);
        border-radius: 0.5em;
    }

    progress[value]::-webkit-progress-value {
        background-color: var(--c-pink);
        border-radius: 0.5em;
    }

    label {
        height: 85%;
    }
</style>