<template>
  <div class="container column">
    <app-form @defineBlock="addBlock"></app-form>
    <app-resume :blocks="blocks"></app-resume>
  </div>
  <app-comments :api="API"></app-comments>
</template>

<script>
import AppForm from '@/AppForm'
import AppResume from '@/AppResume'
import AppComments from '@/AppComments'

export default {
  data () {
    return {
      API: 'https://jsonplaceholder.typicode.com/comments?_limit=42',
      blocks: []
    }
  },
  methods: {
    addBlock (type, text) {
      const typeComponent = 'App' + type.charAt().toUpperCase() + type.slice(1)
      this.blocks.push({
        type: typeComponent,
        text
      })
    }
  },
  components: {
    AppForm,
    AppResume,
    AppComments
  }
}
</script>

<style>

</style>
