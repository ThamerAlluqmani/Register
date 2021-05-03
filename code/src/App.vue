<template>
  <form  @submit="onSubmit">
  <div class="container">
    <div class="input-wrapper">
      <custom-input name="Username" :value="username.value" :rules="{required:true , min:4}" type="text" @onUpdate="onUpdate"/>
      <custom-input name="Email" :value="email.value" :rules="{required:true , pattren : /^[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,4}$/ }" type="email" @onUpdate="onUpdate"/>
      <custom-input name="Password" :value="password.value" :rules="{required:true , min:8}" type="password" @onUpdate="onUpdate"/>
      <custom-input ref="Password" name="Repeat Password" :value="repeat_password.value" :rules="{required:true , same:true}" type="password" @onUpdate="onUpdate"/>

      <custom-button text="Register"
                     color="white"
                     background-color="#49a09d"
                     :disabled="!valid"
      />
    </div>
  </div>
  </form>
</template>

<script>
import CustomButton from "./components/CustomButton.vue";
import CustomInput from "./components/CustomInput.vue";

export default {
  components: {CustomButton, CustomInput},
  data() {
    return {
      username: {
        value: '',
        valid: false
      } ,
      email: {
        value: '',
        valid: false
      }
      ,
      password: {
        value: '',
        valid: false
      },
      repeat_password: {
        value: '',
        valid: false,

      },

    }
  },
  methods: {
    onUpdate(data) {
      this[data.name.toLowerCase().replace(' ' , '_')] = data;
    },
    onSubmit(ev){
      ev.preventDefault();
    }
  },
  computed: {
    valid() {
      return this.username.valid && this.password.valid  && this.email.valid && this.repeat_password.valid
    }
  }
}
</script>

<style scoped>
.input-wrapper{
  display: flex;
  justify-content: space-between;
  flex-direction: column;
  width: 50%;
  padding: 5%;

}

</style>
