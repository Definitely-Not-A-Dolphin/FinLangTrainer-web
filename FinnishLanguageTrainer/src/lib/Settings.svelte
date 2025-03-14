<script lang="ts">
  // Language
  let setLanguage: string = "Finnish";

  const setEnglish = () => {
    setLanguage = "English";
  };
  const setFinnish = () => {
    setLanguage = "Finnish";
  };

  // Wordtype

  // Amount of words
  let wordAmount: number = 6;

  const AddOne = () => {
    wordAmount += 1;
  };
  const SubtractOne = () => {
    wordAmount -= 1;
    if (wordAmount === 0) {
      wordAmount = 1;
    };
  };

  // Random
  let random: boolean = true
  let randomText: string = ""
  const setRandomTrue = () => {
    random = true;
    randomText = ""
  };
  const setRandomFalse = () => {
    random = false;
    randomText = "not ";
  };
</script>

<h2>Settings</h2>

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
  <button onclick={SubtractOne}>Subtract one</button>
  <button onclick={AddOne}>Add one</button>
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