<script>
export default {
  data() {
    return {
      qualidades: [
        { qualidade: 5, desempenho: "5% (Péssimo)" },
        { qualidade: 10, desempenho: "10% (Ruim)" },
        { qualidade: 15, desempenho: "15% (OK)" },
        { qualidade: 20, desempenho: "20% (Bom)" },
        { qualidade: 25, desempenho: "25% (Muito Bom)" },
        { qualidade: 30, desempenho: "30% (Excelente)" },
      ],
      valor: 0,
      pessoa: 1,
      qualidade_selecionada: "",
    };
  },
  computed: {
    valor_final() {
      return (
        (this.valor * (1 + this.qualidade_selecionada / 100)) /
        this.pessoa
      ).toFixed(2);
    },
  },
};
</script>
<template>
  <main>
    <div class="calc">
      <h1>Calculadora de Gorjetas</h1>
      <div class="valores-forms">
        <label for="input-valor">Qual o valor da conta?</label>
        <input v-model="valor" placeholder="0" id="input-valor" type="number" />
      </div>
      <div class="valores-forms">
        <label for="select-desempenho">Como foi o serviço?</label>
        <select
          v-model="qualidade_selecionada"
          name="select-qualidade"
          id="select-desempenho"
        >
          <option disabled value="">Escolha a sua gorjeta</option>
          <option
            v-for="qualidade of qualidades"
            :key="qualidade.qualidade"
            for="select-desempenho"
            :value="qualidade.qualidade"
          >
            {{ qualidade.desempenho }}
          </option>
        </select>
      </div>
      <div class="valores-forms">
        <label for="input-pessoas"
          >Quantas pessoas estão pagando a conta?</label
        >
        <input
          v-model="pessoa"
          placeholder="1"
          id="input-pessoas"
          type="number"
        />
      </div>
    </div>
    <div class="resultado">
      <h2>Valor da conta:</h2>
      <span>R$ {{ valor_final }} por pessoa</span>
    </div>
  </main>
</template>
