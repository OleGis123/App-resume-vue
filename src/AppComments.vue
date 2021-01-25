<template>
  <div class="container">
    <p>
      <button class="btn primary" @click="loadComments">Загрузить комментарии</button>
    </p>
    <app-loader v-if="loading"></app-loader>
    <app-comment
      v-if="showComments"
      :comments="comments"
    ></app-comment>
  </div>
</template>

<script>
import AppLoader from './AppLoader'
import AppComment from '@/AppComment'

export default {
  props: {
    api: String
  },
  components: {
    AppLoader,
    AppComment
  },
  data () {
    return {
      comments: [],
      loading: false,
      showComments: false
    }
  },
  methods: {
    async loadComments () {
      this.loading = true
      const response = await fetch(this.api, { method: 'GET' })
      this.comments = await response.json()
      this.loading = false
      this.showComments = true
    }
  }
}
</script>

<style scoped>

</style>
