<template>
  <form className="card card-w30">
    <div className="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="blockType">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div className="form-control">
      <label htmlFor="value">Значение</label>
      <textarea id="value" rows="3" v-model="blockValue"></textarea>
    </div>

    <button className="btn primary"
        @click.prevent="sendBlock"
        :disabled="isDisabled"
    >
      Добавить
    </button>
  </form>

</template>

<script>
export default {
  emits: ['addBlockEvent'],
  data() {
    return {
      blockType: 'title',
      blockValue: ''
    }
  },
  methods: {
    sendBlock() {
      this.$emit('addBlockEvent', {type: this.blockType, value: this.blockValue})
      this.blockType = 'title'
      this.blockValue = ''
    }
  },
  computed: {
    isDisabled() {
      return (this.blockValue.length < 5)
    }
  },
}
</script>

<style scoped>

</style>