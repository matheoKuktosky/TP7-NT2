<template>

  <div id="navigator">
		<button id="reset" v-on:click="reset"> {{ getResetBtnTxt }} </button>
		<span id="message"> {{ message }} </span>

		<button id="easy" v-on:click="handleDificultyChanged(false)" :class="!isHard ? 'selected' : ''">easy</button>
		<button id="hard" v-on:click="handleDificultyChanged(true)" :class="isHard ? 'selected' : ''">hard</button>
	</div>

</template>

<script lang="js">

  export default  {
    name: 'Navigator',
    props: {
        message: String,
		restart: Function,
    },
    data () {
      return {
		isHard: true
      }
    },
    methods: {
		handleDificultyChanged(isHard){
			if(this.isHard !== isHard){
				this.isHard = isHard
				this.restart(isHard)
			}
		},
		reset(){
			this.restart(this.isHard)
		}
    },
    computed: {
        getResetBtnTxt: function () {
            return this.message === 'You Picked Right!' ? 'Play Again!' : 'New colors!'  
        }
    }
}


</script>

<style scoped lang="css">
#navigator {

	background: #ffffff;
	height: 30px;
	text-align: center;
	margin: 0;
	margin-top: -30px;

}

button {
	border: none;
	background-color: white;
	font-family: "Montserrat", "Avenir";
	text-transform: uppercase;
	height: 100%;
	font-weight: 700;
	letter-spacing: 1px;
	color: steelblue;
	transition: all 0.3s;
	outline: none;
}
button:hover {
	color: white;
	background-color: steelblue;
}

#message {
	display: inline-block;
	width: 20%;
}

.selected {
	background-color: steelblue;
	color: white;
}
</style>