<script>
    export let name;
    export let email;
    export let job;
    export let salary;
</script>

<div class="card">
    <div class="user">
        <p>Name: {name}</p>
        <p>Email: {email}</p>
        <p>Job: {job}</p>
        {#if salary == 1000}
            <p>Gehalt: Zu viel</p>
        {:else if salary > 0}
            <p>Gehalt: {salary} €</p>
        {:else}
            <p>Gehalt: Kein</p>
        {/if}
    </div>
</div>