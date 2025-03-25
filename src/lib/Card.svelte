<script>
  import { CardLayout } from "../utils/constants";
  import quotation from "../assets/quotation.svg";
  const { image, name, title, comment, position } = $props();
  const layout = $state(CardLayout);
</script>

<article class="card {layout[position % layout.length]}">
  {#if layout[position % layout.length] === layout[0]}
    <img class="quotation" alt="Quote Pattern" src={quotation} />
  {/if}
  <div class="card__header">
    <img class="card__image" src={image} alt={name} />
    <div class="card__header__names">
      <span class="name">{name}</span>
      <span class="verified">Verified Graduate</span>
    </div>
  </div>
  <p class="card__title t__title">
    {title}
  </p>
  <p class="card__comment">
    {comment}
  </p>
</article>

<style>
  .quotation {
    position: absolute;
    top: 0px;
    right: 80px;
    width: 104px;
    height: 102px;
  }
  .t__title {
    font-weight: 600;
    font-size: 20px;
  }
  .card {
    position: relative;
    margin: auto 24px;
    grid-column: 1 / span 4;
    border-radius: 8px;
    padding: 26px 32px 32px;
    background-color: white;
    box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.3);
  }

  /* Backgrounds colors */
  .card--featured-large {
    background-color: var(--dark-purple);
  }
  .card--medium {
    background-color: var(--dark-blue-gray);
  }
  .card--small {
    background-color: white;
    color: var(--dark-blue-gray);
  }
  .card--large {
    background-color: var(--deep-indigo);
  }

  .card__header {
    display: flex;
    flex-direction: row;
    
  }

  .card__image {
    width: 28px;
    height: 28px;
    border: 2px solid var(--light-purple);
    border-radius: 50%;
  }

  .card__header__names {
    margin-left: 17px;
    display: flex;
    flex-direction: column;
  }
  .card__header__names > .name {
    margin-top: 4px;
    font-style: normal;
  }

  .card__header__names > .verified {
    margin-top: 4px;
    opacity: 0.5;
  }

  .card__title {
    position: relative;
    margin-top: 18px;
  }

  .card__comment {
    color: var(--pale-gray);
    margin-top: 40px;
    opacity: 0.7;
  }

  .card--small > .card__comment {
    color: var(--dark-blue-gray);
  }

  @media screen and (min-width: 1440px) {
    .card {
      margin: 0;
    }
    .card--featured-large {
      grid-column: 1 / span 6;
    }
    .card--medium {
      grid-column: 7 / span 3;
    }
    .card--small {
      grid-column: 1 / span 3;
    }
    .card--large {
      grid-column: 4 / span 6;
    }
    .card--small.vertical {
      grid-column: 10 / span 3;
      grid-row: 1 / span 2;
    }
  }
</style>
