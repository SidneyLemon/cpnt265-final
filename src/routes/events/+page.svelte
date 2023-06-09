<script>
  import { fade } from "svelte/transition";
  import { elasticOut } from "svelte/easing";

  let visible = true;

  function spin(node, { duration }) {
    return {
      duration,
      css: (t) => {
        const eased = elasticOut(t);

        return `
        transform: scale(${eased}) rotate(${eased * 1080}deg);
        color: hsl(
          ${Math.trunc(t * 360)},
          ${Math.min(100, 1000 - 1000 * t)}%,
          ${Math.min(50, 500 - 500 * t)}%
        );`;
      },
      outro: (node, { duration }) => {
        return {
          duration,
          css: (t) => {
            const eased = elasticOut(1 - t);

            return `
            transform: scale(${eased}) rotate(${eased * 1080}deg);
            color: hsl(
              ${Math.trunc((1 - t) * 360)},
              ${Math.min(100, 1000 - 1000 * (1 - t))}%,
              ${Math.min(50, 500 - 500 * (1 - t))}%
            );`;
          },
        };
      },
    };
  }
  //************************************************************/
  //3. SVELTE ANIMATIONS:
  //The two animations below are timed using duration. When the first spinning animation fades out, the second button animation fades in. Upon clicking the button will redirect user to the contact page
  //************************************************************/
</script>

{#if visible}
  <div class="centered" in:spin={{ duration: 3000 }} out:fade>
    <span>BOOK!</span>
  </div>

  <div class="centered" in:fade={{ duration: 8000 }} out:fade>
    <span>
      <button class="cta">
        <a href="contact">Get in Touch!</a>
      </button></span
    >
  </div>
{/if}

<main>
  <h1>Book an Event!</h1>
  <article>
    <p>
      Welcome to our events page, where you can find all the latest happenings
      at our pizza restaurant. From pizza-making classes to live music nights,
      we have a variety of events that are sure to satisfy your appetite for
      fun. Our pizza-making classes are a great way to learn the art of
      pizza-making from our expert chefs, and you get to enjoy your delicious
      creations afterwards. Our live music nights are the perfect opportunity to
      enjoy great food and drinks while listening to talented local musicians.
      We also offer themed events such as trivia nights and game nights, perfect
      for a fun evening with friends or family. Keep an eye on this page for
      updates on upcoming events, and be sure to follow us on social media to
      stay up to date with all the exciting things happening at our restaurant.
    </p>

    <p>
      <em
        >We can't wait to see you at our next event and serve you our delicious
        pizzas!</em
      >
    </p>
  </article>
</main>

<style>
  .centered {
    position: absolute;
    left: 50%;
    top: 80%;
    transform: translate(-50%, -50%);
  }

  span {
    position: absolute;
    transform: translate(-50%, -50%);
    font-size: 3em;
  }

  .button-container {
    text-align: center;
    margin-top: -7.5%;
    margin-right: 55%;
  }
  button {
    width: 8rem;
    background-color: white;
    border-radius: 1rem;
  }

  main {
    background: black;
    width: 100%;
    height: 100%;
    height: 42rem;
  }

  article {
    margin-top: 1rem;
    margin-left: 12.5rem;
    padding-top: 1rem;
    padding-right: 1rem;
    width: 65%;
    padding: 2rem;
    border-radius: 2rem;
    text-align: center;
    font-size: 18px;
    color: white;
    letter-spacing: 0.02em;
    background: rgb(179, 10, 10);
  }
  h1 {
    color: white;
    margin-top: 1rem;
    margin-left: 0rem;
    padding: 1rem;
    text-align: center;
    font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
    letter-spacing: 0.2em;
  }

  @media only screen and (max-width: 600px) {
    article {
      margin-left: auto;
      margin-right: auto;
      width: 80%;
      height: 44%;
      overflow-y: hidden;
    }
    p {
      margin-left: auto;
      margin-right: auto;
      width: 100%;
      height: 100%;
      overflow: hidden;
    }
  }
</style>
