<script lang="ts">
  import UserCard from "$lib/components/cards/user-card.svelte";
  import { onMount } from "svelte";
  let users: [] = [];

  onMount(async () => {
    users = await getUsers();
  });

  const getUsers = async () => {
    const response = await fetch("https://dummyjson.com/users");
    const data = await response.json();
    return data.users;
  };
</script>

<div
  class="grid xl:grid-cols-5 lg:grid-cols-4 md:grid-cols-4 sm:grid-cols-3 grid-cols-2 gap-4"
>
  {#if !users.length}
    {#each [1, 2, 3, 4, 5, 6, 7, 8, 9] as i}
      <div
        class="bg-secondary p-4 shadow-lg rounded-lg flex flex-col gap-4 animate-pulse"
      >
        <div class="bg-primary rounded-lg shadow-lg w-100 h-44 animate-pulse" />
        <div
          class="rounded-full w-full h-6 bg-primary shadow-lg animate-pulse"
        />
        <div
          class="rounded-full w-1/2 h-6 bg-primary shadow-lg animate-pulse"
        />
      </div>
    {/each}
  {/if}
  {#each users as user}
    <UserCard {user} />
  {/each}
</div>
