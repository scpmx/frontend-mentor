<script lang="ts">

    import { getDrawerStore } from "@skeletonlabs/skeleton";

    const drawerStore = getDrawerStore();

    function drawerClose(): void {
        drawerStore.close();
    }

    let pages = [
        { name: "Home", path: "/"},
        { name: "Results Summary", path: "/results-summary"}
    ]
</script>

<nav class="list-nav p-4">
    <ul>
        {#each pages as page}
            <li><a href="{page.path}" on:click={drawerClose}>{page.name}</a></li>
        {/each}
    </ul>
</nav>