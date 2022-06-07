<template>
  <div>
    <h1>Calculadora</h1>
    <Calculadora />
  </div>
</template>

<script>
import Calculadora from "./main/Calculadora"

export default {
  components: { Calculadora }
};
</script>

<style>
@font-face{
  font-family: "RobotoMono";
  src: url("./fonts/RobotoMono-Thin.ttf");
}
*{
  font-family: "RobotoMono",monospace;
}
body{
  margin:0;
}
#app {
  display:flex;
  flex-direction: column;
  height: flex;
  justify-content: center;
  align-items: center;
  text-align: center;

  color: #fff;
  background: linear-gradient(to right, rgba(83,105,118), rgb(41,46,73));

}
</style>
