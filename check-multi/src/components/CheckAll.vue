<template>
  <div>
    <span class="title" v-if="clickAll" @click="clearCheck">取消</span>
    <span class="title" v-else @click="checkAll">全选</span>

    <div class="one-item" v-for="(item, index) in List" :key="index">
      <div class="item-r" ref="liId">
        <span class="date">{{ item.time }}</span>
        <!-- 时间 -->
        <span class="image-item">{{ item.name }}</span>
        <!-- 项目名字 -->
      </div>
      <div @click="choosed(index)">
        <img v-if="checkBox.includes(index)" :src="imgUrl" class="select" />
        <div v-else class="no-select" ></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CheckAll",
  data() {
    return {
      List: [
        { time: "20210112", name: "zss" },
        { time: "20210110", name: "ls" },
        { time: "20210113", name: "hhh" },
      ], // 选项集合
      checkBox: [], // 选中的内容
      clickAll: false, // 是否全选,
      imgUrl: require("../assets/dui.png")
    };
  },
  methods: {
    // 多选
    async choosed(index) {
     var idx = this.checkBox.indexOf(index);
      if (!this.checkBox.includes(index)) {
        this.checkBox.push(index);
        console.log(this.checkBox);
        
        if(this.checkBox.length == this.List.length){
          this.clickAll = true;
        }
      } else if(this.checkBox.includes(index)){
        this.checkBox.splice(idx, 1);
        this.clickAll = false;
      }
    },
    //全选
    async checkAll() {
      var len = this.List.length;
      this.checkBox = [];
      for (var i = 0; i < len; i++) {
        this.checkBox.push(i);
      }
      this.clickAll = true;
    },
    // 取消全选
    async clearCheck() {
      this.checkBox = [];
      this.clickAll = false;
    },
  },
};
</script>

<style scoped>
.title {
  width: 10px;
  height: 10px;
  background: lightblue;
  border: 1px solid black;
}
.one-item {
  margin-top: 15px;
  display: flex;
  width: 150px;
  height: 50px;
  /* border:1px solid red; */
  justify-content: space-between;
}
.item-r {
  width: 130px;
  height: 50px;
  border: 1px solid blue;
  border-radius: 10px;
}
.choose {
  width: 130px;
  height: 50px;
  border: 1px solid green;
  border-radius: 10px;
}
.no-select {
  margin-top: 2px;
  width: 17px;
  height: 17px;
  border: 1px solid pink;
  border-radius: 10px;
}
.select {
  width: 17px;
  height: 17px;
  border-radius: 10px;
}
</style>