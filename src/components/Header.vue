<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {
  name: 'MyHeader',
  props: { title: String },
};
</script>
