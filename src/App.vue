<template lang="pug">
  #app
    .pantalla
      input.texto(type="text" v-model="contenido")
    .botones
      .fila1
        button(@click="agregar('(')") (
        button(@click="agregar(')')") )
        button() nada
        button(@click="borrarTodo") c
        button(@click="borrarUno") borrar
      
      .fila2
        button(@click="agregar(7)") 7
        button(@click="agregar(8)") 8
        button(@click="agregar(9)") 9
        button(@click="agregar('/')") /
        button(@click="agregar('x')") &times;
      
      .fila3
        button(@click="agregar(4)") 4
        button(@click="agregar(5)") 5
        button(@click="agregar(6)") 6
        button(@click="agregar('-')") -
        button(@click="agregar('+')") +
      
      .fila4
        button(@click="agregar(1)") 1
        button(@click="agregar(2)") 2
        button(@click="agregar(3)") 3
        button(@click="agregar('.')") .
        button(@click="agregar('%')") %
      
      .fila5
        button.cero(@click="agregar(0)") 0
        button.igual() =
      //- .numericos
      //-   button 9
      //-   button 8
      //-   button 7
      //-   button 6
      //-   button 5
      //-   button 4
      //-   button 3
      //-   button 2
      //-   button 1
      //-   button 0
      //- .operaciones
      //-   button &times;
      //-   button /
      //-   button +
      //-   button -
      //-   button %
      //- .accion
      //-   button c
      //-   button borrar
      //-   button =
      //- .simbolos
      //-   button (
      //-   button )
      //-   button .
      
        

</template>

<script>

export default {
  name: 'app',
  data () {
    return {
      contenido: ''
    }
  },
  methods: {
    agregar (caracter) {
      this.contenido += caracter
    },
    borrarUno () {
      this.contenido = this.contenido.slice(0, -1)
    },
    borrarTodo () {
      this.contenido = ''
    }
  }
}
</script>

<style lang="scss">
*{
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
body{
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
input{
  width: 250px;
  height: 50px;
  text-align: right;
  display: inline-block;
  font-size: 20px;
}

button{
  height: 50px;
  width: 50px;
  display: inline-block;
}
.cero{
  width: 150px;
}
.igual{
  width: 100px;
}
</style>
