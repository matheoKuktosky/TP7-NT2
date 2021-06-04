<template>
  <div id="app">
    <Header :pickedColor="pickedColor" :hasWon="hasWon"/>
    <Navigator :message="message" :restart="restart"/>
    <Container :colors="colors" :pickedColor="pickedColor" :hasWon="hasWon" :getMessage="getMessage"/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Navigator from './components/Navigator.vue'
import Container from './components/Container.vue'

export default {
  name: 'App',
  components: {
    Header,
    Navigator,
    Container,    
  },
  mounted () {
    this.restart(true)
  },
  data() {
    return{
        colorCount : 6,
        isHard : true,
        colors : [],
        pickedColor : '',
        message: '',
    }
  },
  methods: {
    randomInt(){
      return Math.floor(Math.random() * 256);
    },

    createRandomStringColor(){
      let newColor = "rgb(" + this.randomInt() + ", " + this.randomInt() + ", " + this.randomInt() + ")" 
      return newColor
    },

    PickColor(){
      let quantity
      if (this.isHard) {
        quantity = 6
      } else {
        quantity = 3
      }
      return Math.floor(Math.random() * quantity )
    },

    createNewColors(numbers){
      let arr = []
      for (let i = 0; i < numbers; i++) {
        arr.push(this.createRandomStringColor())
      }
        return arr
    },

    restart(hardDificulty){
        this.isHard = hardDificulty
        this.colorCount = hardDificulty ? 6 : 3
        this.colors = this.createNewColors(this.colorCount)
        this.pickedColor = this.colors[this.PickColor()]
        this.message = ''
      },

    getMessage(message) {
        return this.message = message
    }    
  },
  computed: {
    hasWon: function () {
      return this.message === 'You Picked Right!'
    }
  }

}
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
body{
  background: #232323;
	margin: 0;
	font-family: "Montserrat", "Avenir";
}
</style>
