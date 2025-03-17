<script lang="ts">
  import words from "../jsonfiles/wordsFile.json";

  let wordsArray = $state(words.wordsArray);

  function randomInt(min: number, max: number): number {
    return Math.floor(Math.random() * (max - min + 1)) + min;
  }

  const nextWord = () => {
    continuePractise = true;
    inputText = "";
    submitted = false;
    index = randomInt(1, 3);
    counter++;
  };

  let practise: boolean = $state(false);
  let index: number = $state(randomInt(1, 3));
  let counter: number = $state(0);

  let engWord: string = $state(wordsArray[index][0]);
  let finWord: string = $state(wordsArray[index][1]);

  let continuePractise: boolean = $state(false);
  let submitted: boolean = $state(false);
  let correct: boolean = $state(false);

  let inputText: string = $state("");

  const submitAnswer = () => {
    submitted = true;
    if (inputText === finWord) {
      correct = true;
    } else {
      correct = false;
    }
  };

  // Settings

  // Language
  let setLanguage: string = $state("Finnish");

  const setEnglish = () => {
    setLanguage = "English";
  };
  const setFinnish = () => {
    setLanguage = "Finnish";
  };

  // Amount of words
  let wordAmount: number = $state(6);

  // Random
  let random: boolean = true;
  let randomText: string = $state("");
  const setRandomTrue = () => {
    random = true;
    randomText = "";
  };
  const setRandomFalse = () => {
    random = false;
    randomText = "not ";
  };

  const commencePractise = () => {
    practise = true;
  };
</script>

{#if practise}
  <div class="item practise">
    <p>
      Question {counter}: give the finnish word for {engWord}:
    </p>

    <input bind:value={inputText} />
    <button onclick={submitAnswer}>Submit</button>

    {#if submitted}
      {#if correct}
        <p>Correct :D</p>
      {:else}
        <p>Incorrect :(</p>
      {/if}
      <button onclick={nextWord}>Next</button>
    {/if}
  </div>
{/if}

{#if !practise}
  <div class="item main">
    <h2>Settings</h2>

    <button onclick={commencePractise}>Start</button>

    <h3 class="nob">Language</h3>
    <p class="not">
      Click on the language that you want to practise:
      <button onclick={setEnglish}>English</button>
      <button onclick={setFinnish}>Finnish</button>
      <br />
      The current language is {setLanguage}
    </p>

    <h3 class="nob">Word Amount</h3>
    <p class="not">
      Give the amount of words you would like to practise:
      <input type="number" bind:value={wordAmount} min="1" max="36" />
      <br />
      The current word amount is {wordAmount}
    </p>

    <h3 class="nob">Random Order</h3>
    <p class="not">
      Would you like to randomise the word order?
      <button onclick={setRandomTrue}>Yes</button>
      <button onclick={setRandomFalse}>No</button>
      <br />
      The word order is {randomText}randomised.
    </p>
  </div>
{/if}
