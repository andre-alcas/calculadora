<template>
    <div>
        <Textarea v-model="value" disabled rows="5" cols="30" />
    </div>
</template>

<script>

export default {
    props: ['value'],
}
</script>

<style>
.textarea {
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
</style>