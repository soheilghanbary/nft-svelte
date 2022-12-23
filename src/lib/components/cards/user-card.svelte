<script lang="ts">
  import { blur } from "svelte/transition";
  import { goto } from "$app/navigation";
  export let user: any;
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<div
  on:click={() => goto(`/users/${user.id}`)}
  class="p-4 shadow-lg rounded-lg bg-secondary hover:ring-2 ring-blue duration-200 cursor-pointer active:scale-90"
>
  <figure>
    <img
      src={user.image}
      draggable="false"
      alt={user.maidenName}
      decoding="async"
      class="rounded-lg shadow-md"
      loading="eager|lazy"
      transition:blur
    />
  </figure>

  <div
    class="flex flex-col gap-1 xl:text-sm lg:text-sm md:text-sm text-xs mt-4"
  >
    <h2 class="font-medium text-base">
      {user.firstName + " " + user.lastName}
    </h2>
    <p class="opacity-80 break-words">{user.email}</p>
  </div>
</div>
