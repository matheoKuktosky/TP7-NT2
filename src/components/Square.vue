<template>
    <div class="square" :style="{ background: color }" v-on:click="handleClick(color)">

    </div>
</template>

<script lang="js">

  export default  {
    name: 'Square',
    props: {
        color: String,
        pickedColor: String,
        getMessage: Function,
    },
    mounted () {
    },
    data () {
      return {

      }
    },
    methods: {
        handleClick(color){            
            if(color === this.pickedColor){
                this.getMessage('You Picked Right!')
            }
            else{
                this.color = "#232323"
                this.getMessage('Try Again!')
            }
        },
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
#colorDisplay {
	font-size: 200%;
}


.square {
	width: 30%;
	background: blue;
	padding-bottom: 30%;
	float: left;
	margin: 1.66%;
	border-radius: 10%;
	transition: background 0.8s;
	-webkit-transition: background 0.8s;
	-moz-transition: background 0.8s;

}
</style>