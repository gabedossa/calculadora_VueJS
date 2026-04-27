<template>
  <div class="calculadora">
    <h1>Calculadora</h1>

    <div class="form">
      <div class="campo">
        <label for="numero1">Número 1</label>
        <input
          id="numero1"
          v-model.number="numero1"
          type="number"
          placeholder="Digite o primeiro número"
        />
      </div>

      <div class="campo">
        <label for="operacao">Operação</label>
        <select id="operacao" v-model="operacao">
          <option value="+">+ Adição</option>
          <option value="-">− Subtração</option>
          <option value="*">× Multiplicação</option>
          <option value="/">÷ Divisão</option>
        </select>
      </div>

      <div class="campo">
        <label for="numero2">Número 2</label>
        <input
          id="numero2"
          v-model.number="numero2"
          type="number"
          placeholder="Digite o segundo número"
        />
      </div>
    </div>

    <div class="resultado">
      <span class="expressao">{{ numero1 }} {{ operacao }} {{ numero2 }} =</span>
      <span class="valor" :class="{ erro: erro }">{{ resultado }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Calculadora',
  data() {
    return {
      numero1: 0,
      numero2: 0,
      operacao: '+',
    }
  },
  computed: {
    erro() {
      return this.operacao === '/' && this.numero2 === 0
    },
    resultado() {
      if (this.erro) return 'Divisão por zero'

      switch (this.operacao) {
        case '+': return this.numero1 + this.numero2
        case '-': return this.numero1 - this.numero2
        case '*': return this.numero1 * this.numero2
        case '/': return this.numero1 / this.numero2
        default:  return 0
      }
    },
  },
}
</script>

<style scoped>
.calculadora {
  max-width: 480px;
  margin: 60px auto;
  background: #1e1e2e;
  border-radius: 16px;
  padding: 40px 36px;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.4);
  font-family: 'Segoe UI', sans-serif;
  color: #cdd6f4;
}

h1 {
  text-align: center;
  font-size: 1.6rem;
  margin-bottom: 32px;
  letter-spacing: 1px;
  color: #cba6f7;
}

.form {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.campo {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

label {
  font-size: 0.85rem;
  color: #a6adc8;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

input,
select {
  background: #313244;
  border: 1.5px solid #45475a;
  border-radius: 8px;
  color: #cdd6f4;
  font-size: 1.1rem;
  padding: 10px 14px;
  outline: none;
  transition: border-color 0.2s;
}

input:focus,
select:focus {
  border-color: #cba6f7;
}

select option {
  background: #313244;
}

.resultado {
  margin-top: 36px;
  background: #313244;
  border-radius: 12px;
  padding: 20px 24px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
  flex-wrap: wrap;
}

.expressao {
  color: #a6adc8;
  font-size: 1rem;
}

.valor {
  font-size: 1.8rem;
  font-weight: 700;
  color: #a6e3a1;
}

.valor.erro {
  color: #f38ba8;
  font-size: 1.1rem;
}
</style>
