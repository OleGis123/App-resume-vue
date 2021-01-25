<template>
  <div class="card card-w70">
    <h3 v-if="blocks.length === 0">Добавьте первый блок, чтобы увидеть результат</h3>
    <component
      v-else
      v-for="item in blocks"
      :is="item.type"
      :text="item.text"
      :key="item"
    ></component>
  </div>
</template>

<script>
import AppTitle from '@/AppTitle'
import AppSubtitle from '@/AppSubtitle'
import AppAvatar from '@/AppAvatar'
import AppText from '@/AppText'

export default {
  props: {
    blocks: Array
  },
  components: {
    AppTitle,
    AppSubtitle,
    AppAvatar,
    AppText
  }
}
</script>

<style scoped>

</style>
