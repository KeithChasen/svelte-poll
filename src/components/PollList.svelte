<script>
    import { onMount, onDestroy } from 'svelte';
    import PollStore from "../stores/PollStore";
    import PollDetails from "./PollDetails.svelte";
    export let polls = [];

    PollStore.subscribe(data => {
       polls = data;
    });

    onMount(() => {
       console.log('component mounted')
    });

    onDestroy(() => {
        console.log('component destroyed');
    })

</script>

<div class="poll-list">
    {#each polls as poll (poll.id)}
        <PollDetails {poll} on:vote/>
    {/each}
</div>

<style>
    .poll-list {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }
</style>
