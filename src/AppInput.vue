<template>
  <div class="form-control" :class="{ invalid: error }">
    <label :for="id">{{ label }}</label><br>
    <input 
      type="text" 
      :id="id"
      :placeholder="placeholder"
      :value="modelValue"
      @input="onChange"
    />
    <small v-if="error">{{ error }}</small>
  </div>
</template> 

<script>
export default {
  emits: ['update:modelValue'],
  props: {
    placeholder: {
      type: String,
      default: ''
    },
    label: {
      type: String,
      default: ''
    },
    error: {
      type: String,
      default: ''
    },
    modelValue: String
  },
  methods: {
    onChange (event) {
      this.$emit('update:modelValue', event.target.value)
    }
  },
  data () {
    return {
      id: 'input-' + Math.random()
    }
  }
}
</script>

<style scoped>
.form-control {
  margin-bottom: 1rem;
}
.form-control.invalid input {
  border: 1px solid red;
}
.form-control small {
  color: red;
}
</style>
