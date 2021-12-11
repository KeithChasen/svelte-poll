<script>
    import { fade, scale } from 'svelte/transition';
    import { onMount, onDestroy } from 'svelte';
    import PollStore from "../stores/PollStore";
    import PollDetails from "./PollDetails.svelte";

    onMount(() => {
       console.log('component mounted')
    });

    onDestroy(() => {
        console.log('component destroyed');
    })

</script>

<div class="poll-list">
    {#each $PollStore as poll (poll.id)}
<!--         svelte transitions are allowed only for html tags-->
<!--         |local means it will be triggered only in case one particular poll is deleted-->
        <div in:fade out:scale|local>
            <PollDetails {poll} />
        </div>
    {/each}
</div>

<style>
    .poll-list {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }
</style>
