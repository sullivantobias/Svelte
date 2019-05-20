<script>
  import Test from "./Test.svelte";
  let count = 0;
  let clicked = false;

  $: double = count * 2;
  $: triple = count * 3;
  $: totalTest = [];

  const handleClick = e => {
    clicked = !clicked;
    count++;
    totalTest = [...totalTest, count];
  };
</script>

<style>
  button {
    padding: 10px;
  }

  .clicked {
    background-color: black;
    color: white;
  }

  .item {
    display: inline;
    margin-right: 10px;
  }
</style>

<button on:click|preventDefault={handleClick} class:clicked>Add Test</button>

{#if totalTest.length}
  <h1>Total</h1>
  {#each totalTest as test}
    <p class="item">{test}</p>
  {/each}
{/if}

<Test test={count} />

<p>Double is {double}</p>
<p>Triple is {triple}</p>
