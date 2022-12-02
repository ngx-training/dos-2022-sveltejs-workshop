<script>
    import Card from './lib/Card.svelte';
  import Header from './lib/Header.svelte';
  import User from './lib/User.svelte';
  import UserForm from './lib/UserForm.svelte';

  const user = {
    name: 'Gregor',
    email: 'gregor@doroschenko.dev',
    job: 'Developer',
    phone: '123456',
    salary: 98
  };

  const userList = [
    { id: 1, name: 'User 1', email: 'user1@test.com', job: 'Developer', salary: 1000 },
    { id: 2, name: 'User 2', email: 'user2@test.com', job: 'QA Engineer', salary: 10000 },
    { id: 3, name: 'User 3', email: 'user3@test.com', job: 'Project Manager', salary: 500 },
  ];

  const apiResponsePromise = fetch('https://ngx-training.com/categories').then(response => response.json());

  function callBackFunction(event) {
    const { name, email } = event.detail;
    alert(name + ' ' + email);
  }

  let cardVisible = true;
  function hideCard() {
    cardVisible = false;
  }
</script>

<main>
  <Header />
  <!-- <UserForm bind:userVaue={user} /> -->
  <!--<UserForm bind:name={user.name} bind:email={user.email} on:saveUser={callBackFunction} />-->
  {#if cardVisible}
  <Card title="Overwritten">
    <p>Card body</p>
    <svelte:fragment slot="action">
      <button>Card Action</button>
      <button>Card Action 2</button>
    </svelte:fragment>
    <p>Card body 3</p>
    <p slot="header">Header title</p>
    <p>Card body 2</p>
  </Card>
  {/if}

  <button on:click={hideCard}>Hide Card</button>

  <!--<User {...user} />-->

  <!--
  <div class="userList">
    {#each userList as userItem }
      <User {...userItem} />
    {:else}
      <p>Keine Nutzer</p>
    {/each}
  </div>
  -->

  <!--
  {#await apiResponsePromise}
    <p>Es lädt...</p>
  {:then responseData} 
  <div class="userList">
    {#each responseData as { name, description, published_at } }
      {@const formattedDate = new Date(published_at).toLocaleDateString()}
      <p>{name}: {description} - published at: {formattedDate}</p>
    {:else}
      <p>Keine Kategorien</p>
    {/each}
  </div>
  {:catch error}
    {@debug error}
  {/await}
  -->
</main>