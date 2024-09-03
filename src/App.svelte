<script>

  import usersData from './users.json';

  // Initialize state for the selected user
  let users = usersData;
  let selectedUser = '';
  let selectedIndex = null;
  let isLoading = false; 


  function chooseRandomUser() {
    isLoading = true;
    setTimeout(() => {
      const randomIndex = Math.floor(Math.random() * users.length);
      selectedUser = users[randomIndex];
      selectedIndex = randomIndex + 1;
      isLoading = false;
    }, 12000); 
  }
</script>

<style>

</style>
<div class="container">
  <h1>Azubis Jobs</h1>
  <h3>Список участников</h3>


  <ul>
    {#each users as user, index}
       <li>{index + 1}. {user}</li>
    {/each}
 </ul>


  <button on:click={chooseRandomUser}>Случайный выбор</button>


  <div class="loader {isLoading ? 'active' : ''}">
    <img src="./src/static/assets/loader1.gif" alt="Loading...">
  </div>


  {#if selectedUser}
      <h2>Случайно выбранный участник: <br> Номер - {selectedIndex}. <br> Аккаунт в Instagram - {selectedUser}</h2>
   {/if}
</div>