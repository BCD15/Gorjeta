<script>
export default {
  data() {
    return {
      valorConta: 0,
      Gorjeta: 15,
      numPessoas: 1,
    };
  },
  methods: {
    calcular() {
      const valorConta = this.valorConta;
      const Gorjeta = this.Gorjeta;
      const numPessoas = this.numPessoas;
      let valorGorjeta = 0;
      let valorTotal = {};
      valorGorjeta = valorConta * (Gorjeta / 100);
      valorTotal = (valorConta + valorGorjeta) / numPessoas;
      // valorTotal = Math.round(valorTotal * 100) / 100;
      valorTotal = valorTotal.toFixed(2);
      console.log(valorTotal);
      document.getElementById("resultado").innerHTML = valorTotal;
    },
  },
};
</script>

<template>
  <main>
    <div class="calculadora">
      <form>
        <h1>Calculadora de Gorjetas</h1>
        <label>
          <p>Valor da Conta:</p>
          <input type="number" v-model="valorConta" id="valorConta" />
        </label>
        <label>
          <p>Qualidade do Serviço:</p>
          <select class="estrela" v-model="Gorjeta" id="valorGorjeta">
            <option value="30">5 ★<!-- 30% (Excepcional) --></option>
            <option value="25">4 ★<!-- 25% (Mais do que bom) --></option>
            <option value="20">3 ★<!-- 20% (Bom) --></option>
            <option value="15">2 ★<!-- 15% (Ok) --></option>
            <option value="10">1 ★<!-- 10% (Ruim) --></option>
            <option value="5">0★ <!-- 5% (Péssimo) --></option>
          </select>
        </label>
        <label>
          <p>Número de pessoas para dividir a conta:</p>
          <input v-model="numPessoas" type="number" id="numPessoas" />
        </label>
        <label>
          <br>
          <button type="button" @click="calcular">
            Calcular valor por pessoa
          </button>
          <div class="resultado">
            R$:<span id="resultado">0.00</span>
          </div>
        </label>
      </form>
    </div>
  </main>
</template>
