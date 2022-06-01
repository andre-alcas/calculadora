<template>
  <display class="display">
    {{ value }}
  </display>
</template>

<script>
export default {
  props: ['value'],
};
</script>

<style>
.display {
  grid-column: span 4;
}
</style>