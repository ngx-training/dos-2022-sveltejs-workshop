<script>
    import { createEventDispatcher, onMount } from 'svelte';

    export let name;
    export let email;

    let active = true;

    const dispatch = createEventDispatcher();

    const submitHandler = () => {
        const newUser = { name, email };
        dispatch('saveUser', newUser, { cancelable: true });
    }

    let buttonElement;

    onMount(() => {
        console.log(buttonElement);
    })
</script>

<div class="userForm" class:active>
    <form on:submit|preventDefault={submitHandler}>
        <input type="text" bind:value={name}>
        <input type="text" bind:value={email}>
        <button type="submit">Save user</button>
    </form>

    <p>Name: {name}, Email: {email}</p>

    <button bind:this={buttonElement}>Click</button>
    <button on:click>Forward Click Event</button>
</div>