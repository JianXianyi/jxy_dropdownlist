<template>
  <div class="dropdown-list" ref="list">
    <dropdown-list-item
      v-for="(item, index) in listData"
      :key="item.text + index"
      :data-text="item.text"
      :data-val="item.value"
    ></dropdown-list-item>
    <div
      class="list-item"
      @click="addNewItem"
    >
      +
    </div>
  </div>
</template>

<script>
import DropdownListItem from "./DropdownListItem.vue";
import DropInput from "./DropInput.vue";
export default {
  components: { DropdownListItem, DropInput },
  name: "DropdownList",
  data() {
    return {
      currentText: this.listData[0].text,
      currentVal: this.listData[0].value,
    };
  },
  props: {
    listData: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  methods:{
    addNewItem(){
      this.$bus.$emit('showBox')
    }
  },
  mounted() {
    // const div = document.createElement("div");
    // const add = document.createElement("span");
    // div.className = "list-item";
    // add.innerText = "+";
    // div.appendChild(add);
    // this.$refs.list.appendChild(div);
  },
};
</script>

<style scoped>
.dropdown-list {
  border: 1px solid #ddd;
  border-radius: 10px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.dropdown-list :last-child {
  border-bottom: none !important;
}
</style>