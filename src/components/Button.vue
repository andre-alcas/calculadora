<template>
  <Button class="button" :class="{ double, triple, operation }">
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
:root{
    --bg-button: #f0f0f0;
}

.button.double{
    grid-column: span 2;
}
.button.triple{
    grid-column: span 3;
}
.button.operation{
    background-color: #f0f0f0;
}

</style>