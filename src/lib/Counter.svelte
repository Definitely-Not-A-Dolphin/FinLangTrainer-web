<script lang="ts">
  let count: number = 0;
  const increment = () => {
    count += 1;
  };
</script>

<button class="button1" onclick={increment}>
  count is {count}
</button>
