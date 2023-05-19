<template>
    <div>
        <h1>Vue con TypeScript</h1>
        <button @click='aumentarContador'>Aumentar</button>
        <h2>Contador: {{ contador }}</h2>
    </div>
</template>

<script lang="ts">
  import Vue from 'vue';
  
  export default Vue.extend({
    name: 'firstComponent',
    data() {
      return {
        contador: 0
      }
    },
    methods: {
      aumentarContador(): Number {
        return this.contador++;
      }
    }
  });
</script>
<style scoped>
</style>