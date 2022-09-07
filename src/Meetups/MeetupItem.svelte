<script>
  import { createEventDispatcher } from "svelte";
  import Button from "../UI/Button.svelte";

  export let id;
  export let title;
  export let subtitle;
  export let imageURL;
  export let description;
  export let emailAddress;
  export let address;
  export let isFavorite;

  const dispatch = createEventDispatcher();
</script>

<article>
  <header>
    <h1>{title}</h1>
    <h2>{subtitle}</h2>
    <p>{address}</p>
  </header>
  <div class="image">
    <img src={imageURL} alt={title} />
  </div>
  <div class="content">
    <p>{description}</p>
  </div>
  <footer>
    <Button href="mailto:{emailAddress}" caption="Contact" />
    <Button
      mode="outline"
      type="button"
      caption={isFavorite ? "Unfavorite" : "Favorite"}
      on:click={() => dispatch("toggleFavorite", id)}
    />
    <Button type="button" caption="Show Details" />
  </footer>
</article>

<style>
  article {
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    border-radius: 5px;
    background: white;
    margin: 1rem;
  }

  header,
  .content,
  footer {
    padding: 1rem;
  }

  .image {
    width: 100%;
    height: 14rem;
  }

  .image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  h1 {
    font-size: 1.25rem;
    margin: 0.5rem 0;
    font-family: "Roboto Slab", sans-serif;
  }

  h2 {
    font-size: 1rem;
    color: #808080;
    margin: 0.5rem 0;
  }

  p {
    font-size: 1.25rem;
    margin: 0;
  }

  div {
    text-align: right;
  }
</style>
