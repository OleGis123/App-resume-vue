<template>
  <form class="card card-w30" @submit.prevent="addBlock">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="type">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea id="value" rows="3" v-model.trim="text"></textarea>
    </div>

    <button class="btn primary" :disabled="lengthText" >Добавить</button>
  </form>

</template>

<script>
export default {
  emits: ['defineBlock'],
  data () {
    return {
      text: '',
      type: 'title'
    }
  },
  methods: {
    addBlock () {
      this.$emit('defineBlock', this.type, this.text)
      this.text = ''
      this.type = 'title'
    }
  },
  computed: {
    lengthText () {
      return this.text.length <= 3
    }
  }
}
</script>

<style scoped>

</style>
