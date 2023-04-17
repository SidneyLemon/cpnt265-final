<script>
  import { pizzas } from "$lib/pizzas.js";
  import Card from "$lib//Card.svelte";
</script>

<main>
  <section>
    {#each pizzas as pizza}
      <a href="menu/{pizza.id}">
        <Card {pizza} />
      </a>
    {/each}
  </section>
</main>
