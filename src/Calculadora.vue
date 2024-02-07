
<script>

  export default {
    data() {
      return {
        number1: 0,
        number2: 0,
        operation: 'add',
        result: 0,
        error: '',
      };
    },
    methods: {
      calculate() {
        this.error = ''; 
        const num1 = parseFloat(this.number1);
        const num2 = parseFloat(this.number2);

        if (isNaN(num1) || isNaN(num2)) {
          this.error = 'Por favor, insira números válidos.';
          return;
        }

        switch (this.operation) {
          case 'add':
            this.result = num1 + num2;
            break;
          case 'subtract':
            this.result = num1 - num2;
            break;
          case 'multiply':
            this.result = num1 * num2;
            break;
          case 'divide':
            if (num2 === 0) {
              this.error = 'Erro: Divisão por zero';
            } else {
              this.result = num1 / num2;
            }
            break;
          default:
            this.error = 'Operação inválida';
            break;
        }
      },
    },
  };

</script>

<template>
  <div id="app">
    <div class="glass-container">
      <div class="calculator glass-effect inputGroup">
        <h1>Calculadora</h1>
        <input type="number" v-model="number1" @input="calculate" />
        <select v-model="operation" @change="calculate">
          <option value="add">+</option>
          <option value="subtract">-</option>
          <option value="multiply">*</option>
          <option value="divide">/</option>
        </select>
        <input type="number" v-model="number2" @input="calculate" />
        <p v-if="error">{{ error }}</p>
        <p v-else>Resultado: {{ result }}</p>
      </div>
    </div>
  </div>

</template>

<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');

#app{
  font-family: 'Poppins', sans-serif;
}

p {
  font-size: 18px;
  color:#925a90;
}

.glass-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color:#ffe2ff; 
}

.calculator {
  text-align: center;
  padding: 20px;
  border-radius: 10px;
  background-color: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(10px); 
}

.glass-effect {
  box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
  backdrop-filter: blur(4px);
  border-radius: 10px;
}

.inputGroup input,
select{
  font-size: 20px;
  padding: 5px;
  outline: none;
  border: 2px solid rgb(200, 200, 200);
  width: 100px;
  margin: 5px;
  
}
select{
  text-align: center;
}
</style>
