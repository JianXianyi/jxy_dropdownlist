<template>
  <div class="list-item" @click="changeInp(dataText,dataVal)" :value="dataVal">
      {{dataText}}
  </div>
</template>

<script>
export default {
    name:"DropdownListItem",
    props:{
        dataText:{
            type:String,
            default(){
                return ''
            }
        },
        dataVal:{
            type:String,
            default(){
                return ''
            }
        }
    },
    methods:{
        //修改input框内的文字
        changeInp(dataText,dataVal){
            this.$bus.$emit("changeInp",dataText,dataVal)
        }
    }
}
</script>

<style>
    .list-item{
        width: 80%;
        text-align: center;
        height: 30px;
        line-height: 30px;
        border-bottom: 1px solid #ddd;
        cursor: pointer;
    }
</style>