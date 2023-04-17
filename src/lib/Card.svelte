<script>
  export let pizza;
</script>

<article class="card">
  <img src="/{pizza.images}" width="300" height="300" alt="pizza images" />

  <a href={pizza.url} target="_blank">
    <h3>{pizza.title}</h3>
    <p>{pizza.description}</p>
  </a>
</article>

<style>
  article {
    width: 100%;
    margin: 0;
    border-radius: 1px rgb(8, 8, 8);
    box-shadow: 0 2px 2px rgb(179, 10, 10);
    align-items: center;
  }
  article :hover {
    background-color: rgb(179, 10, 10);
    color: white;
    text-decoration: none;
  }

  article img {
    display: block;
    width: 100%;
    object-fit: cover;
  }

  .card {
    display: grid;
    margin: 0;
    grid-gap: 2em;
  }
  @media (min-width: 60em) {
    .card {
      grid-template-columns: repeat(3, 1fr);
      margin: 0;
      max-width: 1500px;
    }
  }
</style>
