<script>
    import Sidebar from "./sidebar.svelte";
    import Check from "./check.svelte";

    export let principes;
    export let principe;
    export let url;

</script>

<Check {principe} {url} />
<Sidebar {principes}/>