<template>
  <button
    class="btn"
    @click="handleClick()"
    :style="{ backgroundColor: color }"
  >
    {{ label }}
  </button>
</template>

<script>
export default {
  name: 'MyButton',
  props: {
    label: String,
    color: String,
  },
  methods: {
    handleClick() {
      this.$emit('btn-click');
    },
  },
};
</script>
