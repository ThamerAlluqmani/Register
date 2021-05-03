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
button:disabled:hover{
  opacity:.5 ;
  filter: brightness(100%);

}
button{
  width: 100%;
  border: none;
  padding: 10pt;
  border-radius: 5pt;
}
button:hover{
  filter: brightness(150%);
}
</style>
