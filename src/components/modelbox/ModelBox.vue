<template>
  <div class="box" v-show="ShowBox">
    <span class="close" @click="changeShow">close</span>
    <div class="text">
      <label for="text">text</label>
      <input type="text" name="text" id="text" v-model="text" />
    </div>
    <div class="val">
      <label for="value">value</label>
      <input type="text" name="value" id="value" v-model="val" />
    </div>
    <div class="add">
        <button @click="add">add</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ModelBox",
  data() {
    return {
      ShowBox: false,
      text:'',
      val:''
    };
  },
  mounted() {
    this.$bus.$on("showBox", () => {
      this.ShowBox = !this.ShowBox;
    });
  },
  methods: {
    changeShow() {
      this.$bus.$emit("showList");
      this.ShowBox = !this.ShowBox;
    },
    add(){
        this.$bus.$emit('addItem',this.text,this.val)
      this.ShowBox = !this.ShowBox;

    }
  },
};
</script>

<style scoped>
.box {
  position: absolute;
  z-index: 8;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 300px;
  height: 300px;
  border-radius: 10px;
  background-color: #fff;
}
.close {
  cursor: pointer;
}
*{
    margin:10px;
}
</style>