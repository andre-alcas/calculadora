<template>
  <div class="display1">
    {{ value }}
  </div>
    <div class="display">
    {{ value }}
  </div>
</template>

<script>
export default {
  props: ['value'],
};
</script>

<style>
.display {
  grid-column: span 4;
  background-color: #D3D3D3;

  display: flex;
  justify-content:flex-end;
  align-items: center;
  padding: 20px;
  font-size: 2.1em;
  color: #000000;
  overflow: hidden;
  text-overflow: hidden;
  
}
.display1 {
  grid-column: span 4;
  background-color: #D3D3D3;

  display: flex;
  justify-content:flex-end;
  align-items: center;
  padding: 10px;
  font-size: 1.0em;
  color: #000000;
  overflow: hidden;
  text-overflow: hidden;
  
}
</style>