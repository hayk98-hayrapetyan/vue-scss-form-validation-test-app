<template>
  <div>
    <input
      :type="type"
      :placeholder="placeholder"
      v-model.trim="modelValue"
    />
    <span v-if="error">{{error}}</span>
  </div>
</template>

<script>
export default {
  name: 'BaseInput',
  props: {
    type: {
      type: String,
      default: 'text'
    },
    placeholder: String,
    value: {
      type: String
    },
    validators: Array
  },
  model: {
    prop: 'value',
    event: 'input'
  },
  data: () => ({
    error: null
  }),
  computed: {
    modelValue: {
      get(){
        return this.value
      },
      set(val){
        this.$emit('input', val);
      }
    },
  },
  watch: {
    validators: {
      handler(val){
        const res = val.find(e => e.error);
        this.error = res ? res.message : null;
      },
      deep: true
    }
  }
}
</script>

<style lang="scss" scoped>
div {
  margin: 0 auto 30px;
  input {
    width: 100%;
    max-width: 100%;
    border: 1px solid $gray;
    outline: none;
    background: transparent;
    padding: 8px 12px;
    box-sizing: border-box;
  }
  span {
    font-size: 12px;
    color: red;
  }
  @include mQ(600px){
    margin: 0 auto 15px;
  }
}
</style>