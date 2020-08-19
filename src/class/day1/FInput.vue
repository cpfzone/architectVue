<template>
  <div>
    <input :value="value" @input="onInput" v-bind="$attrs" />
  </div>
</template>

<script>
export default {
  // 防止外层的div继承attrs
  inheritAttrs: false,
  props: {
    value: {
      type: String
    }
  },
  methods: {
    onInput(e) {
      // 通知父组件数值变化
      this.$emit("input", e.target.value)
      // 通知父组件进行校验
      this.$parent.$emit("validate")
    }
  }
}
</script>

<style scoped>
</style>