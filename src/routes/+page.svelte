<script lang="ts">
  import data from "../lib/words.json" with { type: "json" };

  function randomInt(min: number, max: number): number {
    return Math.floor(Math.random() * (max - min + 1)) + min;
  }

  // Settings
  let wordAmount: number = 6;


  let index: number = $state(1);
  let engword: string = $derived(data.array[index][0]);
  let finWord: string = $derived(data.array[index][1]);
  let input: string = $state("");

  let practising: boolean = $state(false);
  let submitted: boolean = $state(false);
  let correct: boolean = $state(false);
  let wordCount: number = $state(1);

  const startPractising = () => {
    practising = true;
    index = randomInt(2, data.array.length);
  };
  const submitAnswer = () => {
    submitted = true;
    if (input === finWord) {
      correct = true;
    } else {
      correct = false;
    }
  };
  const nextWord = () => {
    input = "";
    submitted = false;
    correct = false;
    wordCount += 1;
    index = randomInt(1, data.array.length - 1);
  };
  const endPractising = () => {
    input = "";
    submitted = false;
    correct = false;
    practising = false;
    wordCount = 1;
    index = 1;
  };
</script>

<div class="header">
  <h1>Title</h1>
</div>

{#if !practising}
  <div class="main">
    <h2>Settings</h2>

    <button onclick={startPractising}> Start </button>
  </div>
{/if}

{#if practising}
  <div class="main">
    <h2>Practising</h2>

    <p>Question {wordCount}: translate {engword}</p>
    <input bind:value={input} />
    {#if !submitted}
      <button onclick={submitAnswer}>Submit</button>
    {/if}

    {#if submitted}
      {#if correct}
        <p>Correct :D</p>
      {:else}
        <p>Incorrect :(</p>
      {/if}

      {#if wordCount === 3}
        <button onclick={endPractising}>Next</button>
      {:else}
        <button onclick={nextWord}>Next</button>
      {/if}
    {/if}
  </div>
{/if}

<div class="main">
  <h1>Debug Panel</h1>

  <p>
    index: {index} <br />
    engword: {engword} <br />
    finword: {finWord} <br />
    input: {input}
  </p>
  <p>
    practising: {practising} <br />
    submitted: {submitted} <br />
    correct: {correct} <br />
    wordCount: {wordCount}
  </p>
</div>
