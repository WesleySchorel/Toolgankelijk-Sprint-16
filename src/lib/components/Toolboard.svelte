<script>
	import Checklist from "$lib/components/Checklist.svelte";
	import Sidebar from "$lib/components/Sidebar.svelte";
    

    export let url;
    export let principe;
    export let principes;
    
</script>

<Checklist {url} {principe}/>
<Sidebar {principes}/>
