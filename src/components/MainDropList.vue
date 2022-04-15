<template>
  <div class="main-list">
    <drop-input
      @showTime="changeStatus"
      :currentText="currentText"
      :currentVal="currentVal"
    ></drop-input>
    <dropdown-list
      @changeInp="changeInp"
      :list-data="listData"
      v-show="showList"
    ></dropdown-list>
  </div>
</template>

<script>
import DropdownList from "./dropdown/DropdownList.vue";
import DropInput from "./dropdown/DropInput.vue";
export default {
  name: "MainDropList",

  data() {
    return {
      currentText: this.listData[0].text?this.listData[0].text:'====无====',
      currentVal: this.listData[0].value?this.listData[0].value:'',
      showList: false,
    };
  },
  methods: {
    changeStatus() {
      this.showList = !this.showList;
    },
    changeInp(text, val) {
      
    },
  },
  mounted(){
      this.$bus.$on("changeInp", (text, val) => {
        //   console.log(text,val)
          this.currentText=text;
          this.currentVal=val;
          this.showList = !this.showList;
        // refresh();
      });
  },
  props: {
    listData: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  components: {
    DropdownList,
    DropInput,
  },
};
</script>

<style scoped>
    *{
        font-size: 12px;
    }
</style>