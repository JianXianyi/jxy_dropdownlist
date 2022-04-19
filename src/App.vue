<template>
  <div class="ap">
    <div :class="mainClass ? 'black' : 'white'"></div>
    <main-drop-list :listData="listData"></main-drop-list>
  </div>
</template>

<script>
import MainDropList from "./components/MainDropList.vue";
export default {
  name: "App",
  data() {
    return {
      listData: [
        { text: "香蕉", value: "one" },
        { text: "苹果", value: "two" },
        { text: "水蜜桃", value: "three" },
        { text: "火龙果", value: "four" },
        { text: "荔枝", value: "five" },
        { text: "山竹", value: "six" },
      ],
      mainClass: false,
    };
  },
  components: {
    MainDropList,
  },
  mounted() {
    this.$bus.$on("showBox", () => {
      this.mainClass = !this.mainClass;
    });
    this.$bus.$on("showList", () => {
      this.mainClass = !this.mainClass;
    });
    this.$bus.$on("addItem", (text, val) => {
      this.listData.push({ text, value: val });
      this.mainClass = !this.mainClass;
    });
  },
};
</script>

<style>
.black {
  position: absolute;
  z-index: 2;
  width: 100vw;
  height: 100vh;
  background-color: #000;
  opacity: 0.5;
}
</style>
