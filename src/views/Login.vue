<template>
  <div class="wrapper">
    <h1>Sign In</h1>
    <form @submit.prevent="submit">
      <BaseInput
        v-for="(input, i) in form"
        :key="i"
        :placeholder="input.placeholder"
        :type="input.type"
        :value="input.value"
        :validators="input.validators"
        v-model="input.value"
      />
      <BaseButton />
    </form>
  </div>
</template>

<script>
import BaseInput from "@/components/ui/BaseInput";
import BaseButton from "@/components/ui/BaseButton";

export default {
  components: { BaseInput, BaseButton },
  data: () => ({
    form: {
      name: {
        placeholder: 'Name',
        value: '',
        validators: [
          {
            test: /^[a-zA-Z]+$/,
            message: 'Please write only letters',
            error: false
          }
        ]
      },
      surname: {
        placeholder: 'Surname',
        value: '',
        validators: [
          {
            test: /^[a-zA-Z]+$/,
            message: 'Please write only letters',
            error: false
          }
        ]
      },
      email: {
        placeholder: 'Email',
        value: '',
        validators: [
          {
            test: /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/,
            message: 'Please write valid email address',
            error: false
          }
        ]
      },
      phone: {
        placeholder: 'Phone',
        value: '',
        validators: [
          {
            test: /^\+?[0-9 ]+$/,
            message: 'Please write valid phone number',
            error: false
          },
        ]
      },
      password: {
        placeholder: 'password',
        value: '',
        type: 'password',
        validators: [
          {
            test: /^[a-zA-Z0-9](?=.*?[#?!@$%^&*-.+]).{8,}$/,
            message: 'Password must be at least 8 long and contain at least 1 special character',
            error: false
          }
        ]
      }
    }
  }),
  methods: {
    submit(){
      let error = false;
      Object.values(this.form).forEach(input => {
        input.validators.forEach(validator => {
          const reg = validator.test
          const result = reg.test(input.value);
          if(!result){
            error = true
            return validator.error = true
          }
          validator.error = false;
        })
      })
      if(!error) {
        alert('Thanks for testing')
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.wrapper {
  text-align: center;
  padding: 50px 40px;
  h1 {
    font-size: 40px;
    font-weight: bold;
    margin-bottom: 30px;
  }
  form {
    padding: 40px;
    max-width: 500px;
    margin: auto;
    border: 2px solid black;
  }
  @include mQ(600px){
    padding: 30px 15px;
    h1 {
      font-size: 28px;
      margin-bottom: 20px;
    }
    form {
      padding: 15px;
    }
  }
}
</style>