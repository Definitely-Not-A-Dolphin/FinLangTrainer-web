<script lang="ts">
  let finWord: string = "tähti";
  let engWord: string = "star";

  let continuePractise: boolean = $state(false);
  let submitted: boolean = $state(false);
  let correct: boolean = $state(false);

  let inputText: string = $state("");

  const randomInt = (min: number, max: number) => {
    Math.floor(Math.random() * (max - min + 1)) + min;
  };

  const nextWord = () => {
    continuePractise = true;
    inputText = "";
    submitted = false;
  };

  const submitAnswer = () => {
    submitted = true;
    if (inputText === finWord) {
      correct = true;
    } else {
      correct = false;
    }
  };
</script>

<p>
  Give the finnish word for {engWord}:
</p>

<input bind:value={inputText} />
<button onclick={submitAnswer}>Submit</button>

<p id="testding">
  star: {inputText}
</p>

{#if submitted}
  {#if correct}
    <p>Correct :D</p>
  {:else}
    <p>Incorrect :(</p>
  {/if}
{/if}

<button onclick={nextWord}>Next</button>
