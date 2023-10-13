<template>
  <div>
    <select>
      <option value="">Selecciona un país</option>
      <option v-for="pais in paises" :key="pais.id" :value="pais.id">
        {{ pais.name }}
      </option>
    </select>
  </div>
</template>
<script>
  import axios from "axios";

  export default{
    data(){
      return{
        paises: [],

      }
    },

    mounted(){
      this.getPaises();
    },

    methods:{
      async getPaises(){
        try {
        const apiUrl = `http://localhost:8888/api/v1/country`;
        const response = await axios.get(apiUrl);
        this.paises = response.data;
      } catch (error) {
        console.log("Error al obtener paises:", error);
      }
    }
  }
};
  

</script>
