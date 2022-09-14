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
    <div class="submit-bar">
      <h1>Blog App</h1>

      <form action="">
        <input type="text" bind:value={header} />
        <textarea
          name="body_input"
          id="body_input"
          rows="10"
          bind:value={body}
        />
        <button on:click={() => submitBlog(header, body)}>Submit Post</button>
      </form>
    </div>
    <div class="updates">
      {#each headerArr as head, index}
        <Article header={headerArr[index]} body={bodyArr[index]} />
      {/each}
    </div>
  </div>
</main>

<style>
  @media screen and (min-width: 800px) {
    .container {
      display: grid;
      grid-template-columns: 1fr 2fr;
      gap: 2em;
      margin: 1em;
    }
  }

  .submit-bar form {
    display: flex;
    flex-direction: column;
  }

  .submit-bar form input {
    margin: 0.5em;
  }

  .submit-bar form textarea {
    margin: 0.5em;
  }

  .submit-bar form button {
    margin: 0.5em;
    display: flex;
    width: fit-content;
  }

  .updates {
    min-width: 300px;
  }
</style>
