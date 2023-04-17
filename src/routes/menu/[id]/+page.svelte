<script>
  import { page } from "$app/stores";
  import { pizzas } from "$lib/pizzas.js";
  let foundPizza;
  for (let pizza of pizzas) {
    if (pizza.id === $page.params.id) {
      foundPizza = pizza;
      break;
    }
  }
  console.log($page.params.id);
  console.log(foundPizza);
</script>

<main>
  <article class="card">
    <img
      src="/{foundPizza.images}"
      width="600"
      height="600"
      alt="pizza images"
    />

    <a href={foundPizza.url} target="_blank">
      <h3>{foundPizza.title}</h3>
      <p>{foundPizza.description}</p>
    </a>
  </article>
</main>

<style>
  article {
    padding: 1rem;
    display: flex;
    justify-content: center;
    gap: 1rem;
  }
  a {
    margin: 5rem;
    display: block;
    text-decoration: none;
    color: black;
    border-radius: 1rem;
  }
</style>
