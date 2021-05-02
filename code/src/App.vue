<template>
<custom-button text="Register"
               color="black"
               background-color="white"
               :disabled="valid"
/>
</template>

<script>
import CustomButton from "./components/CustomButton.vue";
export default {
  components:{CustomButton},
  data(){
    return {valid:true}
  }
}
</script>

<style scoped>

</style>
