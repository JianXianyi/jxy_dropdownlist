<template>
  <main-drop-list :listData="listData"></main-drop-list>
</template>

<script>
import MainDropList from './components/MainDropList.vue'
export default{
  name: 'App',
  data() {
    return {
      listData:[
        {text:'香蕉',value:'one'},
        {text:'苹果',value:'two'},
        {text:'水蜜桃',value:'three'},
        {text:'火龙果',value:'four'},
        {text:'荔枝',value:'five'},
        {text:'山竹',value:'six'},
      ]
    }
  },
  components:{
    MainDropList
  }
}
</script>

<style>

</style>
