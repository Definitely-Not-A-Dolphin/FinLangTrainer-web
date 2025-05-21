<script lang="ts">
  let { children } = $props();
</script>

<div class="centerer">
  <div class="containerMain">
    {@render children()}
  </div>
</div>
