<template>
  <Button class="button" 
    @click="$emit('onClick',label)"
    :class="{ double, triple, operation }">
    {{ label }}
  </Button>
</template>

<script>
export default {
  props: {
    label: {},
    operation: { type: Boolean },
    double: { type: Boolean },
    triple: { type: Boolean },
  },
};
</script>

<style>
:root {
  --bg-button: #f0f0f0;
}

.button.double {
  grid-column: span 2;
}
.button.triple {
  grid-column: span 3;
}
.button.operation {
  background: linear-gradient(to bottom, #87e0fd 0%,#53cbf1 40%,#05abe0 100%);
}
</style>