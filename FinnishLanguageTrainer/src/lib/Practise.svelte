<script lang="ts">

  let text = $state("");

</script>

<input bind:value={text} />
<button> Submit! </button>

<p id="testding">{text}</p>
