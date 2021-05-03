<template>

    <label :for="name">{{name}}     <span class="error" v-if="error">{{error}}</span></label>

    <input :id="name" :type="type" :value="value" @input="input">

</template>

<script>
export default {
  name: "CustomInput",
  props:{
    name:{type:String , required:true},
    type:{type:String , required:true},
    value:{type:String},
    rules:{type:Object, required:true }
  },
  methods:{
    input(ev){
     this.$emit('onUpdate' , {
       name: this.name,
       value: ev.target.value,
       valid: this.validate(ev.target.value) ? false : true,

     });


    },
    validate(value){
      if (this.rules.required && !value){
        return 'required'
      }
      if (this.rules.min && value.length<this.rules.min){
        return `${this.name} must be more than ${this.rules.min}`
      }
      if (this.rules.pattren && !value.match(this.rules.pattren)){
        return `your email should be like this : example@example.com`
      }

    },

  },
  computed:{
    error(){
      return this.validate(this.value)
    }
  }
}
</script>

<style scoped>
.error{
  color: red;
  font-size: 15pt;
}
input{
  padding: 10px;
  border: 1px solid lightgray;
  border-radius: 5px;
  margin: 10pt 0;
}
label{
  color: white;
  display: flex;
  justify-content: space-between;
}

</style>
