<script>
  import { each, prevent_default } from "svelte/internal";

  import Article from "./lib/Article.svelte";

  let header;
  let body;

  let headerArr =
    JSON.parse(localStorage.getItem("headerArr")) != null
      ? JSON.parse(localStorage.getItem("headerArr"))
      : [];

  let bodyArr =
    JSON.parse(localStorage.getItem("bodyArr")) != null
      ? JSON.parse(localStorage.getItem("bodyArr"))
      : [];

  const submitBlog = (header, body) => {
    headerArr = [...headerArr, header];
    bodyArr = [...bodyArr, body];
    localStorage.setItem("headerArr", JSON.stringify(headerArr));
    localStorage.setItem("bodyArr", JSON.stringify(bodyArr));
  };
</script>

<main>
  <div class="container">
    <div class="left-bar">
      <h1>Blog App</h1>

      <form action="">
        <input type="text" bind:value={header} />
        <input type="text" bind:value={body} />
        <button on:click={() => submitBlog(header, body)}>Submit Post</button>
      </form>
    </div>
    <div class="right-bar">
      {#each headerArr as head, index}
        <Article header={headerArr[index]} body={bodyArr[index]} />
      {/each}
    </div>
  </div>
</main>

<style>
  .container {
    display: grid;
    grid-template-columns: 1fr 4fr;
    gap: 2em;
    margin: 2em;
  }

  .right-bar {
    display: grid;
    gap: 1em;
  }
</style>
