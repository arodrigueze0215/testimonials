<script>
  import Card from "./lib/Card.svelte";
  import { groupTestimonials } from "./api/testimonials";
  const groups = $state(groupTestimonials());
</script>

<main>
  {#each groups as group}
    <div class="container">
      {#each group as testimonial, index}
        <Card
          image={testimonial.image}
          name={testimonial.name}
          title={testimonial.title}
          comment={testimonial.comment}
          position={index}
        />
      {/each}
    </div>
  {/each}
</main>

<style>
  .container {
    margin: 71px 24px;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 24px;
  }

  @media screen and (min-width: 1440px) {
    .container {
      margin: 164px 165px;
      display: grid;
      grid-template-columns: repeat(12, 1fr);
      column-gap: 30px;
    }
  }
</style>
