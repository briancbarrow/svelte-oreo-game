<script>
  let flavors = [
    { name: 'original', visible: false },
    { name: 'birthday cake', visible: false },
    { name: 'pumpkin pie', visible: false },
    { name: 'original', visible: false },
    { name: 'birthday cake', visible: false },
    { name: 'pumpkin pie', visible: false },
    { name: 'original', visible: false },
    { name: 'birthday cake', visible: false },
    { name: 'pumpkin pie', visible: false },
    { name: 'original', visible: false },
    { name: 'birthday cake', visible: false },
    { name: 'pumpkin pie', visible: false }
  ];

  function showAllThings() {
    flavors.forEach((f) => (f.visible = true));
    //svelte is reactive on assignment, so we re-assign flavors to trigger reactivity after the forEach
    flavors = flavors
    setTimeout(() => {
      flavors.forEach((f) => (f.visible = false));
      flavors = flavors
    }, 2000);
  }
</script>

<div class="main">
  <h1>Oreo Game</h1>
  <div class="gameboard">
    {#each flavors as flavor, i}
      <p on:click={() => (flavor.visible = !flavor.visible)}>
        {flavor.visible ? flavor.name : i + 1}
      </p>
    {/each}
  </div>
  <button on:click={() => showAllThings()}>Show All</button>
</div>

<style>
  .main {
    height: 100vh;
    width: 100vw;
    background-color: aqua;
  }

  .gameboard {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
    padding: 1rem;
  }

  .gameboard > p {
    border: 1px solid black;
  }
</style>
