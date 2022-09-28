<script>
  import '../app.css';
  import caramel_coconut from '$lib/images/caramel_coconut.png';
  import birthday_cake from '$lib/images/birthday_cake.png';
  import carrot_cake from '$lib/images/carrot_cake.png';
  import chocolate_hazelnut from '$lib/images/chocolate_hazelnut.png';
  import cinnamon_bun from '$lib/images/cinnamon_bun.png';
  import dark_chocolate from '$lib/images/dark_chocolate.png';
  import java_chip from '$lib/images/java_chip.png';
  import lemon from '$lib/images/lemon.png';
  import neopolitan from '$lib/images/neopolitan.png';
  import peanut_butter_chocolate_pie from '$lib/images/peanut_butter_chocolate_pie.png';
  import pumpkin_spice from '$lib/images/pumpkin_spice.png';
  import toffee_crunch from '$lib/images/toffee_crunch.png';
  let flavors = [
    { name: 'caramel Coconut', visible: false, img: caramel_coconut },
    { name: 'birthday cake', visible: false, img: birthday_cake },
    { name: 'carrot_cake', visible: false, img: carrot_cake },
    { name: 'chocolate hazelnut', visible: false, img: chocolate_hazelnut },
    { name: 'cinnamon bun', visible: false, img: cinnamon_bun },
    { name: 'dark chocolate', visible: false, img: dark_chocolate },
    { name: 'java chip', visible: false, img: java_chip },
    { name: 'lemon', visible: false, img: lemon },
    { name: 'neopolitan', visible: false, img: neopolitan },
    { name: 'peanut butter chocolate pie', visible: false, img: peanut_butter_chocolate_pie },
    { name: 'pumpkin spice', visible: false, img: pumpkin_spice },
    { name: 'toffee crunch', visible: false, img: toffee_crunch }
  ];

  let shown = false;

  function showAllThings() {
    flavors.forEach((f) => (f.visible = !f.visible));
    //svelte is reactive on assignment, so we re-assign flavors to trigger reactivity after the forEach
    flavors = flavors;
    // setTimeout(() => {
    //   flavors.forEach((f) => (f.visible = false));
    //   flavors = flavors;
    // }, 2000);
    shown = !shown;
  }
</script>

<div class="main flex flex-col items-center mt-10 mb-48">
  <!-- <h1>Oreo Game</h1> -->
  <div class="gameboard">
    {#each flavors as flavor, i}
      <!-- <p >
        {flavor.visible ? flavor.name : i + 1}
      </p> -->
      <div
        on:click={() => (flavor.visible = !flavor.visible)}
        class="w-auto flex flex-col overflow-hidden rounded-lg shadow-lg"
      >
        <div class="flex-shrink-0">
          <img
            class="h-52 w-52 object-cover {flavor.visible ? '' : 'hidden'}"
            src={flavor.img}
            alt=""
          />
          <img
            class="h-52 w-52 object-cover {flavor.visible ? 'hidden' : ''}"
            src="https://picsum.photos/200"
            alt=""
          />
        </div>
        <div class="flex flex-1 flex-col justify-between bg-white p-6">
          <div class="flex-1">
            <a href="#" class="mt-2 block">
              <p class="h-14 w-44 text-xl text-center font-semibold text-gray-900">
                {flavor.visible ? flavor.name.toUpperCase() : i + 1}
              </p>
            </a>
          </div>
          <!-- <div class="mt-6 flex items-center">
            <div class="flex-shrink-0">
              <a href="#">
                <span class="sr-only">Roel Aufderehar</span>
                <img class="h-10 w-10 rounded-full" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="">
              </a>
            </div>
            <div class="ml-3">
              <p class="text-sm font-medium text-gray-900">
                <a href="#" class="hover:underline">Roel Aufderehar</a>
              </p>
              <div class="flex space-x-1 text-sm text-gray-500">
                <time datetime="2020-03-16">Mar 16, 2020</time>
                <span aria-hidden="true">&middot;</span>
                <span>6 min read</span>
              </div>
            </div>
          </div> -->
        </div>
      </div>
    {/each}
  </div>
  <button
    class="inline-flex self-center items-center rounded-md border border-transparent bg-indigo-600 px-3 py-2 text-sm font-medium leading-4 text-white shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2"
    on:click={() => showAllThings()}>{shown ? 'Hide All' : 'Show All'}</button
  >
</div>

<style>
  .main {
    height: 100vh;
    width: 100vw;
    background-color: white;
  }

  .gameboard {
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    gap: 1rem;
    padding: 1rem;
  }

  .gameboard > p {
    border: 1px solid black;
  }
</style>
