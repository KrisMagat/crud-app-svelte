<script>
  let list = [
    { id: 'dog', name: 'dog' },
    { id: 'cat', name: 'cat' },
    { id: 'cow', name: 'cow' },
  ];
  let input = null;
  const handleInput = (e) => {
    input = e.target.value;
  };
  const handleSubmit = () => {
    list = [...list, { id: input, name: input }];
    input = null;
  };
  const handleClick = (id) => {
    list = list.filter((item) => item.id != id);
  };
</script>

<main>
  <h3>My List</h3>
  <div class="input">
    <input
      type="text"
      placeholder="Enter item"
      on:input={(e) => handleInput(e)}
      value={input}
    />
    <button on:click={handleSubmit}>Submit</button>
  </div>

  <section class="display">
    {#each list as item (item.id)}
      <div>
        <p>{item.name}</p>
        <button on:click={() => handleClick(item.id)}>X</button>
      </div>
    {:else}
      <p>There are no items to show.</p>
    {/each}
  </section>
</main>

<style>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
  .read-the-docs {
    color: #888;
  }
</style>
