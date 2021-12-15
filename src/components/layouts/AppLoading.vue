<template>
  <div v-if="isLoading" className="loader"></div>
  <slot v-if="!isLoading"></slot>
</template>

<script>
export default {
  data() {
    return {
      isLoading: true
    }
  }
}
</script>
