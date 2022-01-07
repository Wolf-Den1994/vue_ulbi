<template>
<!--  v-show="posts.length"  -->
  <div v-if="posts.length">
    <h3>Список пользователей</h3>
    <post-item
      v-for="post in posts"
      :post="post"
      :key="post.id"
      @remove="$emit('remove', post)"
    />
  </div>
  <!--  v-show="!posts.length"  -->
  <h2
    style="color: red"
    v-else
  >
    Список постов пуст
  </h2>
</template>

<script>
import PostItem from "@/components/PostItem";

export default {
  props: {
    posts: {
      type: Array,
      required: true,
    }
  },
  components: {PostItem}
}
</script>

<style scoped>

</style>