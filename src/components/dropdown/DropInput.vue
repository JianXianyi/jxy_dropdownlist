<template>
  <div class="input" @click="changeStatus">
    <span>{{ currentText }}</span>
    <span>
      <div ref="trangle" class="trangle" @click="changeStatus"></div>
    </span>
  </div>
</template>

<script>
export default {
  name: "DropInput",
  methods: {
    changeStatus() {
      this.$refs.trangle.className =
      this.$refs.trangle.className === "trangle" ? "trangle_up" : "trangle";
      this.$emit("showTime");
    },
  },
  mounted() {
    this.$bus.$on("changeInp", (text, val) => {
      this.$refs.trangle.className =
      this.$refs.trangle.className === "trangle" ? "trangle_up" : "trangle";
    });
  },
  props: {
    currentText: {
      type: String,
      default() {
        return "";
      },
    },
    currentVal: {
      type: String,
      default() {
        return "";
      },
    },
  },
};
</script>

<style scoped>
.input {
  border: 1px solid #ddd;
  border-radius: 10px;
  height: 30px;
  line-height: 30px;
  text-align: center;
  cursor: pointer;
}
.trangle {
  cursor: pointer;
  position: absolute;
  right: 20px;
  top: 20px;
  width: 0px; /*设置宽高为0，所以div的内容为空，从才能形成三角形尖角*/
  height: 0px;
  border-top: 10px solid #ddd;
  border-left: 10px solid transparent; /*transparent 表示透明*/
  border-right: 10px solid transparent;
}
.trangle_up {
  cursor: pointer;
  position: absolute;
  right: 20px;
  top: 20px;
  width: 0px; /*设置宽高为0，所以div的内容为空，从才能形成三角形尖角*/
  height: 0px;
  border-bottom: 10px solid #333;
  border-left: 10px solid transparent; /*transparent 表示透明*/
  border-right: 10px solid transparent;
}
</style>