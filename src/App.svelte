<script lang="ts">
  import Counter from "./lib/Counter.svelte";
  import Settings from "./lib/Settings.svelte";
  import BaldCat from "./assets/BaldCat.jpg";
  import Sizzle from "./assets/Sizzle.jpg";
  import Practise from "./lib/Practise.svelte";
</script>

<main>
  <div class="containerMain">
    <div class="containerCol1">
      <div class="aside1">
        <h1>Check Out:</h1>
      </div>
      <div class="containerCol1a">
        <div class="buttons">
          <button class="button1">My Projects</button>
        </div>
      </div>
    </div>

    <div class="containerCol2">
      <div class="item header">
        <h1 class="not nob">Finnish Language Trainer</h1>
        <p>
          Oh yeah, it's here: the web-version of my first big project. Its not
          done, new features will have to be written in C++ and then
          "translated" to TypeScript, so updates won't happen often :(
        </p>
      </div>

      <div class="item main">
        <Practise />
      </div>

      <div class="item main">
        <Settings />
      </div>

      <div>
        <Counter />
      </div>
    </div>

    <div class="containerCol3">
      <img class="item sizzle" alt="picture of my cat" src={Sizzle} />
      <img class="item sizzle" alt="picture of my friends cat" src={BaldCat} />
    </div>
  </div>
</main>
