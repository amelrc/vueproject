<template>
  <h3>{{name}}<span>({{age}})</span></h3>
</template>

<script>
export default {
  name: 'User',
  props: {
    name: String,
    age: Number,
  },
}
</script>

<style scoped>
span {
  color: #42b983;
}
</style>
