<script>
    import svelteLogo from './../assets/svelte.svg'

    const currentYear = new Date().getFullYear();
</script>

<div class="header">
    <img src={svelteLogo} class="logo svelte" alt="Svelte Logo" />
    <span>DevOpenSpace {currentYear}: Svelte Workshop</span>
</div>

<style>
    .header {
        display: flex;
        flex-direction: row;
        align-items: center;
    }

    .logo {
        margin-right: 1rem;
    }
</style>