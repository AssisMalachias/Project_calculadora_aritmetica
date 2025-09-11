<!-- src/App.vue -->
<script setup>
import { reactive, computed } from 'vue'

// estado reativo
const estado = reactive({
  numero1: 0,
  numero2: 0,
  operacao: 'soma'
})

// cálculo dinâmico
const resultado = computed(() => {
  const { numero1, numero2, operacao } = estado

  switch (operacao) {
    case 'soma':
      return numero1 + numero2
    case 'subtracao':
      return numero1 - numero2
    case 'multiplicacao':
      return numero1 * numero2
    case 'divisao':
      return numero2 !== 0 ? (numero1 / numero2).toFixed(2) : 'Erro: divisão por 0'
    default:
      return 0
  }
})
</script>

<template>
  <div class="container p-5  bg-primary">
    <h1 class=" text-white text-center">Calculadora Aritmética</h1>

    <div class="row mt-4">
      <div class="col-md-3">
        <input
          type="number"
          class="form-control"
          v-model.number="estado.numero1"
          placeholder="Número 1"
        />
      </div>

      <div class="col-md-3">
        <input
          type="number"
          class="form-control"
          v-model.number="estado.numero2"
          placeholder="Número 2"
        />
      </div>

      <div class="col-md-3">
        <select class="form-control" v-model="estado.operacao">
          <option value="soma">Soma (+)</option>
          <option value="subtracao">Subtração (-)</option>
          <option value="multiplicacao">Multiplicação (×)</option>
          <option value="divisao">Divisão (÷)</option>
        </select>
      </div>

      <div class="col-md-3 d-flex align-items-center">
        <h4 class="text-white">= {{ resultado }}</h4>
      </div>
    </div>
  </div>
</template>