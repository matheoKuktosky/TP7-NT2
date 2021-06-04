<template>

<div id="container">

     <ul  v-for="(color, index) in colors" :key="color.id">
         <Square v-if="!hasWon"  :color="colors[index]" :pickedColor="pickedColor" :changeColors="changeColors" :getMessage="getMessage" />
         <Square v-else  :color="pickedColor" :pickedColor="pickedColor" :getMessage="getMessage" />
    </ul>   
</div>

</template>

<script lang="js">
  import Square from './Square.vue'
  export default  {
    name: 'Container',
    components:{ 
        Square
    },
    props: {
        colors: Array,
        pickedColor: String,
        getMessage: Function,
        hasWon: Function,
    },
    mounted () {

    },
    data () {
      return {
      }
    },
    methods: {
    },
    computed: {
    }
}

</script>

<style scoped lang="css">
#container {
	margin: 20px auto;
	max-width: 600px;
}
</style>