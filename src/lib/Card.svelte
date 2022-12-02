<script>
    import { afterUpdate, beforeUpdate, onDestroy, onMount } from "svelte";

    export let title = 'Default Title';

    $: {
        console.log('New Title', title);
    }

    onMount(() => {
        console.log('On Mount called');
    });

    onDestroy(() => {
        console.log('On Destroy called');
    });

    beforeUpdate(() => {
        console.log('BeforeUpdate called');
    })

    afterUpdate(() => {
        console.log('AfterUpdate called');
    })
</script>

<div class="card">
    {#if $$slots.header}
    <div class="card-header">
        <slot name="header"></slot>
        <button>Close</button>
    </div>
    <svelte:self>
        <p>Test</p>
    </svelte:self>
    {/if}
    <div class="card-body">
        <slot></slot>
    </div>
    <div class="card-actions">
        <slot name="action"></slot>
    </div>
</div>

<style>
    .card {
        display: flex;
        flex-direction: column;
    }

    .card-header {
        background-color: rgba(255, 255, 255, 0.5);
    }
</style>