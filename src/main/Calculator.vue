<template>
  <div>
    {{ resultado }}
  </div>
  //TODO: Finalizando 01/06/2022
  <div class="calculator">
    <Display value=""/> 
    <Button label="AC" triple />
    <Button label="/" @click="calcular('dividir')" />
    <Button label="7" value="7" />
    <Button label="8" />
    <Button label="9" />
    <Button label="*" @click="calcular('mult')" />
    <Button label="4" />
    <Button label="5" />
    <Button label="6" />
    <Button label="-" @click="calcular('sub')" />
    <Button label="1" />
    <Button label="2" />
    <Button label="3" />
    <Button label="+" @click="calcular('somar')" />
    <Button label="0" />
    <Button label="=" triple/>
  </div>
</template>

<script>
import Display from "../components/Display";
import Button from "../components/Button";

export default {
  components: { Button, Display },
  data() {
    return {
      resultado: 0,
      value1: 0,
      value2: 0,
    };
  },
  methods: {
    calcular(nomeOperacao) {
      console.log(nomeOperacao);
      switch (nomeOperacao) {
        case (nomeOperacao = "somar"):
          this.value1 = 5;
          this.value2 = 10;
          this.resultado = this.value1 + this.value2;
          alert("Resultado é:" + this.resultado);

          break;

        case (nomeOperacao = "dividir"):
          alert("estou dividindo numeros");
          break;

        case (nomeOperacao = "mult"):
          alert("estou multiplicando numeros");
          break;

        case (nomeOperacao = "sub"):
          alert("estou subtraindo numeros");
          break;

        default:
          break;
      }
    },
  },
};
</script>

<style>
.calculator {
  height: 320px;
  width: 235px;
  border-radius: 5px;
  overflow: hidden;

  display: grid;
  grid-template-columns: repeat(4, 25%);
  grid-template-rows: 1fr 48px 48px 48px 48px 48px;
}
</style>