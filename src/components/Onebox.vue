<template>
<div class="demo">
    <div class="box">
      <ul class="puzzle-wrap">
        <li :class="{'puzzle':true,'puzzle-empty':!puzzle}" v-for="(puzzle,index) in puzzles" v-text="puzzle" :key="puzzle" @click="moveFn(index)">
          
        </li>
      </ul>
    </div>
    <div>
      
    </div>
    <button type="button" @click="luan"> 重新排序</button>
</div>

</template>

<script>
export default {
  name: 'Onebox',
  data(){
    return {
      puzzles:[1,2,3,4,5,6,7,8]
    }
  },
  created(){
    this.luan()
  },
  methods:{
    luan(){
      var arr = JSON.parse(JSON.stringify(this.puzzles))
      var newArr = []
      arr.map(()=>{
        var index = Math.floor(Math.random()*arr.length)
        newArr.push(arr[index])
        arr.splice(index,1)
      })
      this.puzzles  = [...newArr,...arr]
    },
    // 点击方块
        moveFn (index) {
          // 获取点击位置及其上下左右的值
          let curNum = this.puzzles[index],
              leftNum = this.puzzles[index - 1],
              rightNum = this.puzzles[index + 1],
              topNum = this.puzzles[index - 3],
              bottomNum = this.puzzles[index + 3]

          // 和为空的位置交换数值
          if (!leftNum  && index % 3) {
              this.$set(this.puzzles , index - 1, curNum)
              this.$set(this.puzzles,index, '')
          } else if (!rightNum && 2 !== index % 3) {
              console.log('xxx')
              this.$set(this.puzzles,index + 1, curNum)
              this.$set(this.puzzles,index, '')
          } else if (topNum==='') {
              this.$set(this.puzzles,index - 3, curNum)
              this.$set(this.puzzles,index, '')
          } else if (!bottomNum) {
              this.$set(this.puzzles,index + 3, curNum)
              this.$set(this.puzzles,index, '')
          }
      },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

body {
    font-family: Arial, "Microsoft YaHei"; 
}

.box {
    width: 400px;
    margin: 50px auto 0;
}

.puzzle-wrap {
    width: 400px;
    height: 400px;
    margin-bottom: 40px;
    padding: 0;
    background: #ccc;
    list-style: none;
}

.puzzle {
    float: left;
    width: 100px;
    height: 100px;
    font-size: 20px;
    background: #33ccee;
    text-align: center;
    line-height: 100px;
    border: 1px solid #ccc;
    box-shadow: 1px 1px 4px;
    text-shadow: 1px 1px 1px #B9B4B4;
    cursor: pointer;
}

.puzzle-empty {
    background: #ccc;
    box-shadow: inset 2px 2px 18px;
}

.btn-reset {
    box-shadow: inset 2px 2px 18px;
}
</style>
