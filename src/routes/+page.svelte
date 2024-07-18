<main>
  <article class="cta">
    <a href="menu">Order Now!</a>
  </article>
</main>

<style>
  main {
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 75vh;
    background-image: url(/hawaiian.jpg);
    margin: 0;
    background-size: cover;
    background-position: center;
  }

  .cta {
    max-width: 50ch;
    /* border: 20px white; */
    border-radius: 2rem;
    padding: 1rem;
    background-color: white;
    text-decoration: none;
  }
  @media screen and (min-width: 40em) {
    main {
      margin: 0;
    }
  }
</style>
