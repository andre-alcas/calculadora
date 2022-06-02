<template>
  <div class="calculator">
    <Textarea :value="displayValue" />
    <Display :value="displayValue" />
    <Button label="AC" triple @onClick="clearMemory" />
    <Button label="/" @onClick="setOperation" />
    <Button label="7" @onClick="addDigit" />
    <Button label="8" @onClick="addDigit" />
    <Button label="9" @onClick="addDigit" />
    <Button label="*" @onClick="setOperation" />
    <Button label="4" @onClick="addDigit" />
    <Button label="5" @onClick="addDigit" />
    <Button label="6" @onClick="addDigit" />
    <Button label="-" @onClick="setOperation" />
    <Button label="1" @onClick="addDigit" />
    <Button label="2" @onClick="addDigit" />
    <Button label="3" @onClick="addDigit" />
    <Button label="+" @onClick="setOperation" />
    <Button label="0" double @onClick="addDigit" />
    <Button label="." @onClick="addDigit" />
    <Button label="=" @onClick="setOperation" />
  </div>
</template>

<script>
import Display from "../components/Display";
import Button from "../components/Button";

export default {
  components: { Button, Display },
  data: function () {
    return {
      displayValue: "0",
      clearDisplay: false,
      operation: null,
      values: [0, 0],
      current: 0,
    };
  },
  methods: {
    clearMemory() {
      //console.log('LimparMemoria')
      Object.assign(this.$data, this.$options.data());
    },
    setOperation(operation) {
      //console.log('Operacao'+operation)
      //quando é o primeiro número informado operação é setada e o display é resetado
      //e o valor de current(segundo valor do vetor) é esperado
      if (this.current === 0) {
        this.operation = operation;
        this.current = 1;
        this.clearDisplay = true;
      } else {
        const equals = operation === "=";
        const currentOperation = this.operation;
        try {
          this.values[0] = eval(
            `${this.values[0]} ${currentOperation} ${this.values[1]}`
          );
        } catch (e) {
          this.$emit("OnError", e);
        }
        this.values[1] = 0;
        //setar o número de casas decimais(precisao) da calculadora
        this.displayValue = parseFloat(this.values[0]).toFixed(5);
        this.operation = equals ? null : operation;
        this.current = equals ? 0 : 1;
        this.clearDisplay = !equals;
      }
    },
    addDigit(n) {
      //console.log('Digito'+n)
      if (n === "." && this.displayValue.includes(".")) {
        return;
      }
      //limpa o display quando o display já está com 0(já é o padrão dentro de data())
      //ou quando o display = true
      const clearDisplay = this.displayValue === "0" || this.clearDisplay;
      //quando limpa o display o valor atual currentValue pode resetar(clearDisplay) ou pode ser
      //o valor que tá no display(this.displayValue)
      const currentValue = clearDisplay ? "" : this.displayValue;
      //atualiza o valor exibido no display concatenado com o digito n
      const newdisplayValue = currentValue + n;

      //atualiza o valor exibido no display(this.displayValue de data()) com o valor da constante newValue
      this.displayValue = parseFloat(newdisplayValue).toFixed(2);
      this.clearDisplay = false;

      //Alternativa 1
      this.values[this.current] = this.displayValue;

      //Alternativa 2
      /*       if(n !== "."){
        const i = this.current
        const newValue = parseFloat(this.displayValue)
        this.values[i] = newValue

      } */
    },
    /*     calcular(nomeOperacao) {
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
    }, */
  },
};
</script>

<style>
.calculator {
  height: 340px;
  width: 230px;
  border-radius: 5px;
  background-color: #0d89ec;
  overflow: hidden;

  display: grid;
  grid-template-columns: repeat(4, 25%);
  grid-template-rows: 1fr 48px 48px 48px 48px 48px;
}
</style>