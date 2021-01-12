<template>
  <div>
    <ul>
      <li
        v-for="(item, index) of cities"
        :key="index"
        :class="{ checked: index == n }"
        @click="changeList(index)"
      >
        {{ item }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "SoloCheck",
  data() {
    return {
      cities: ["上海", "北京", "广州", "重庆", "西安"],
      n: 0,
    };
  },
  methods: {
    changeList(index) {
        // 把index给n  此时data中的n被改变了 n此时等于index 带上了那个checked的class (应该有更好的解决办法？)
      this.n = index; //this指向app
    },
  },
};
</script>

<style scoped>
body {
  margin: 0;
}
ul {
  padding: 0;
  list-style: none;
  margin: 150px 150px;
}
li {
  width: 80px;
  height: 50px;
  display: inline-block;
  border-radius: 8px;
  border: 1px #000 solid;
  text-align: center;
  line-height: 50px;
  cursor: pointer;
  transition: all 0.3s linear;
  margin-left: 5px;
}
li:hover {
  background-color: #0cf;
  color: #fff;
  border: 1px #fff solid;
}
li.checked {
  background-color: #0cf;
  color: #fff;
  border: 1px #fff solid;
}
</style>
