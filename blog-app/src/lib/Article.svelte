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
    min-width: 300px;
    margin-bottom: 1em;
    margin-top: 1em;
  }

  h3 {
    margin-top: 0.2em;
  }
</style>
