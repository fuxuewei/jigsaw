<template>
<div class="demo">
    <div class="box">
      <ul class="box_list">
        <li :class="{'puzzle':true,'puzzle-empty':!puzzle}" v-for="puzzle in puzzles" v-text="puzzle" :key="puzzle">
          
        </li>
      </ul>
    </div>
    <button type="button" @click="luan"> 重新排序</button>
</div>

</template>

<script>
export default {
  name: 'Onebox',
  data(){
    return {
      puzzles:[1,2,3,4,5,6,7,8,9]
    }
  },
  created(){
    this.luan()
  },
  methods:{
    luan(){
      var arr = JSON.parse(JSON.stringify(this.puzzles))
      var newArr = []
      arr.map((item,index)=>{
        var index = Math.floor(Math.random()*arr.length)
        newArr.push(arr[index])
        arr.splice(index,1)
      })
      this.puzzles  = [...newArr,...arr]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
