<template>
  <div>
    <div class="jumbotron">
      <label>Inserte un texto:</label>
      <input type="text" v-model="value" />
    </div>
    <div v-if="cantidadCaracteres > 0">
      <p>Cantidad de caracteres: {{ cantidadCaracteres }}</p>
      <p>{{ value | codificar }} (codificado)</p>
      <p>{{ value | cambiarAMayusculas }} (Mayúscula)</p>
      <p>{{ value | cambiarAMinusculas }} (Minúscula)</p>
      <p>{{ value | mayusMinus }} (Mayúscula / Minúscula)</p>
      <p>{{ value | minusMayus }} (Minúscula / Mayúscula)</p>
    </div>
    <br/>
    <div>
      <p>Respuestas: 1:b 2:b 3:c 4:b 5:b-c</p>
    </div>
  </div>
</template>

<script lang="js">

export default  {
  name: 'CambioLetras',
  props: [],
  data () {
    return {
      value: "",
    }
  },
  computed: {
      cantidadCaracteres(){
          return this.value.length
      }
  },
   filters: {
     codificar: function(value){
        const vocales = {
          a: "u",
          e: "o",
          o: "e",
          u: "a",
          A: "U",
          E: "O",
          O: "E",
          U: "A"
      }
      return value.split("").map(element => vocales[element] ? vocales[element] : element).join("")
     },
     cambiarAMayusculas: function(value){
      return value.toUpperCase()
     },
     cambiarAMinusculas: function(value){
      return value.toLowerCase()
     },
     mayusMinus: function(value){
      return value.split("").map((e, i) => (i + 1) % 2 == 0 ? e.toLowerCase() : e.toUpperCase()).join("")
     },
     minusMayus: function(value){
       return value.split("").map((e, i) => (i + 1) % 2 == 0 ? e.toUpperCase() : e.toLowerCase()).join("")
     },
   }
  }
</script>

<style scoped lang="css">
.jumbotron {
  padding-top: 30px;
  padding-bottom: 30px;
  background-color: rgb(34, 186, 233);
  color:rgb(255, 255, 255);
}
</style>