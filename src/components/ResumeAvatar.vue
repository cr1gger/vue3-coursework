<template>
  <div className="avatar">
    <img :src="value" alt="">
  </div>
</template>

<script>
export default {
  props: {
    value: String
  }
}
</script>

<style scoped>

</style>