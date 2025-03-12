<script lang="ts">
  let setLanguage: string = "finnish";

  const setEnglish = () => {
    setLanguage = "english";
  };
  const setFinnish = () => {
    setLanguage = "finnish";
  }
</script>

<p>
  Click on the language that you want to practise:
  <button onclick={setEnglish}>English</button>
  <button onclick={setFinnish}>Finnish</button>
  <br>
  Current Language is {setLanguage}
</p>