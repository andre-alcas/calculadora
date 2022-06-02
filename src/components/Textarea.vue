<template>
    <Textarea class="display" disabled />
</template>

<script>
export default {
  props: ['modelValue'],
};
</script>

<style>
.textarea {
  grid-column: span 4;
  background-color: #d3d3d3;

  display: flex;
  justify-content: flex-end;
  align-items: center;
  padding: 20px;
  font-size: 2.1em;
  color: #000000;
  overflow: hidden;
  text-overflow: hidden;
}
</style>