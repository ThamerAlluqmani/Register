<template>
  <button :style="{color,backgroundColor}" :disabled="disabled">{{text}}</button>
</template>

<script>
export default {
name: "CustomButton",
  props:{
    text:{type: String , required: true},
    color:{type:String},
    backgroundColor:{type:String},
    disabled:{type:Boolean , required: true},

  }
}
</script>

<style scoped>
button:disabled{
  opacity:.5 ;
}
</style>
