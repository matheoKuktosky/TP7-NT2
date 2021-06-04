<template>
	<div id="header" :style="{ background: hasWon ?pickedColor : bgColor  }">
		<h1>The Great <br>
			<span id="colorDisplay">{{pickedColor}} </span>
			<br>
			Guessing Game</h1>
	</div>
</template>

<script>
export default {
  name: 'JuegoColores',
  props: {
      pickedColor: String,
      hasWon: Function,
  },
  mounted () {
    },
    data () {
      return {
          bgColor: ""

      }
    },
    methods: {
        restart(){
            this.bgColor = "steelblue"
        }
    },
    computed: {

    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#header {
	transition: all 0.3s;
	background: steelblue;
	text-transform: uppercase;
	text-align: center;
	margin: 0;
	color: white;
}
#colorDisplay {
	font-size: 200%;
}

h1 {
	font-weight: normal;
	line-height: 1.1;
	padding: 20px 0;

}
</style>
