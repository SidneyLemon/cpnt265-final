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
</script>

{#if visible}
  <div class="centered" in:spin={{ duration: 8000 }} out:fade>
    <span>PIZZA PARTY!</span>
  </div>
{/if}

<main>
  <p>
    Welcome to our events page, where you can find all the latest happenings at
    our pizza restaurant. From pizza-making classes to live music nights, we
    have a variety of events that are sure to satisfy your appetite for fun. Our
    pizza-making classes are a great way to learn the art of pizza-making from
    our expert chefs, and you get to enjoy your delicious creations afterwards.
    Our live music nights are the perfect opportunity to enjoy great food and
    drinks while listening to talented local musicians. We also offer themed
    events such as trivia nights and game nights, perfect for a fun evening with
    friends or family. Keep an eye on this page for updates on upcoming events,
    and be sure to follow us on social media to stay up to date with all the
    exciting things happening at our restaurant. We can't wait to see you at our
    next event and serve you our delicious pizzas!
  </p>
  <div class="button-container">
    <button class="cta">
      <a href="contact">Get in Touch!</a>
    </button>
  </div>
</main>

<style>
  .centered {
    position: absolute;
    left: 25%;
    top: 50%;
    transform: translate(-50%, -50%);
  }

  span {
    position: absolute;
    transform: translate(-50%, -50%);
    font-size: 5em;
  }

  .button-container {
    text-align: center;
    margin-top: -7.5%;
    margin-right: 55%;
  }
  p {
    margin-top: 10rem;
    margin-left: 40rem;
    padding-right: 1rem;
    width: 40%;
    padding: 2rem;
    border-radius: 1rem;
    text-align: center;

    font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
    background-color: rgb(179, 10, 10);
  }
</style>
