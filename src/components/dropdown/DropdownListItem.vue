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
        changeInp(dataText,dataVal){
            this.$bus.$emit("changeInp",dataText,dataVal)
        }
    }
}
</script>

<style scoped>
    .list-item{
        width: 80%;
        text-align: center;
        height: 30px;
        line-height: 30px;
        border-bottom: 1px solid #ddd;
        cursor: pointer;
    }
</style>