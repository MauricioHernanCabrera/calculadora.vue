<template lang="pug">
  #app.app
    .titulo
      h1 H. M. C.
    .pantalla
      input.texto(
        type="text" 
        v-model="contenido" 
        disabled
        placeholder="0"
      )
    .botones
      .fila1
        button.normal(@click="agregar('(')") (
        button.normal(@click="agregar(')')") )
        button.normal.icon-reddit(@click="sorpresa()")
        button.raro(@click="borrarTodo") AC
        button.raro(@click="borrarUno") DEL
      
      .fila2
        button.normal(@click="agregar(7)") 7
        button.normal(@click="agregar(8)") 8
        button.normal(@click="agregar(9)") 9
        button.normal(@click="agregar('/')") /
        button.normal(@click="agregar('*')") &times;
      
      .fila3
        button.normal(@click="agregar(4)") 4
        button.normal(@click="agregar(5)") 5
        button.normal(@click="agregar(6)") 6
        button.normal(@click="agregar('-')") -
        button.normal(@click="agregar('+')") +
      
      .fila4
        button.normal(@click="agregar(1)") 1
        button.normal(@click="agregar(2)") 2
        button.normal(@click="agregar(3)") 3
        button.normal(@click="agregar('.')") .
        button.normal(@click="agregar('%')") %
      
      .fila5
        button.normal.cero(@click="agregar(0)") 0
        button.normal.igual(@click="calcularOp") =   
        
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
      if (this.esError()) {
        this.contenido = ''
      }
      this.contenido += caracter
    },
    borrarUno () {
      if (this.esError()) {
        this.contenido = ''
      } else {
        this.contenido = this.contenido.slice(0, -1)
      }
    },
    borrarTodo () {
      this.contenido = ''
    },
    calcularOp () {
      if (this.esError()) {
        this.borrarTodo()
      } else {
        try {
          this.contenido = eval(this.contenido) + ''
        } catch (nada) {
          this.contenido = 'Syntax ERROR'
        }
      }
    },
    esError () {
      if (this.contenido === 'Syntax ERROR') {
        return true
      } else {
        return false
      }
    },
    sorpresa () {
      this.contenido = 'Soy igual que vos...'
      setTimeout(() => {
        this.contenido = 'No sirvo para nada.'
        setTimeout(() => {
          this.borrarTodo()
        }, 3000)
      }, 3000)
    }
  }
}
</script>

<style lang="scss">
*{
  box-sizing: border-box;
  padding: 0;
  margin: 0;
  border: 0;
}
body{
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  font-size: 16px;
  font-family: 'Atomic Age', cursive, sans-serif;
}
.app{
  background: #232b42;
  padding: 60px 20px 20px 20px;
  border-radius: 10px 10px 35px 35px;
  .titulo{
    text-align: center;
    margin-bottom: 6px;
    h1{
      color: #a26682;
      font-size: 2em;
    }
  }
  input{
    color: #637670;
    background: #b4ccb6;
    font-family: 'Atomic Age';
    width: 332px;
    height: 80px;
    font-size: 1.7em;
    text-align: right;
    display: inline-block;
    margin: 4px;
    padding-right: 10px;
    border-radius: 7px;
  }
  button{
    color: #fff;
    font-family: 'Atomic Age';
    font-size: 1.5em;
    font-weight: 700;
    display: inline-block;
    height: 40px;
    width: 60px;
    cursor: pointer;
    border-radius: 7px 7px 10px 10px;
    margin: 4px;
    transition: .1s;
  }
  button:active{
    transform: scale(0.95);
  }
  .botones{
    margin-top: 10px;
    .relleno{
      opacity: 0;
    }
    .raro{
      background: #a26682;
    }
    .cero{
      width: 195px;
    }
    .igual{
      width: 130px;
    }
    .normal{
      background: #5B85A0;
    }
    .icon-reddit{
      font-weight: normal;
    }
    .icon-reddit:active{
      background: #911E1E;
    }
  }
}
@media (max-width: 382px) {
  body{
    font-size: 12.8px;
  }
  .app{
    padding: 48px 16px 16px 16px;
    border-radius: 10px 10px 35px 35px;
    .titulo{
      margin-bottom: 4.8px;
    }
    input{
      width: 265.6px;
      height: 64px;
      margin: 3.2px;
      padding-right: 8px;
      border-radius: 5.6px;
    }
    button{
      height: 32px;
      width: 48px;
      border-radius: 5.6px 5.6px 8px 8px;
      margin: 3.2px;
    }
    .botones{
      margin-top: 8px;
      .cero{
        width: 156px;
      }
      .igual{
        width: 104px;
      }
    }
  }
}
@media (max-width: 306px) {
  body{
    font-size: 10.24px;
  }
  .app{
    padding: 38.4px 12.8px 12.8px 12.8px;
    border-radius: 8px 8px 28px 28px;
    .titulo{
      margin-bottom: 3.84px;
    }
    input{
      width: 212.48px;
      height: 51.2px;
      margin: 2.56px;
      padding-right: 6.4px;
      border-radius: 4.48px;
    }
    button{
      height: 25.6px;
      width: 38.4px;
      border-radius: 4.48px 4.48px 6.4px 6.4px;
      margin: 3.2px;
    }
    .botones{
      margin-top: 6.4px;
      .cero{
        width: 124.8px;
      }
      .igual{
        width: 86.5px;
      }
    }
  }
}
</style>
