<script>
  export let header;
  export let body;
</script>

<main>
  <article>
    <h3>{header}</h3>
    <p>{body}</p>
  </article>
</main>

<style>
  article {
    border: black 1px solid;
    padding: 1em;
    min-width: 300px;
  }
  h3 {
    margin-top: -0.8em;
  }
</style>
