<template>
  <div v-show="posts.length > 0">
    <h3>Список постов</h3>
    <transition-group name="post-list">
      <post-item
        v-for="post in posts"
        :post="post"
        :key="post.id"
        @remove="$emit('remove', post)"
      ></post-item>
    </transition-group>
  </div>
  <h2 v-show="posts.length === 0" style="color: red">Список постов пуст</h2>
</template>
<script>
import PostItem from "@/components/PostItem";
export default {
  components: { PostItem },
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
};
</script>
<style scoped>
.post-list-enter-active,
.post-list-leave-active {
  transition: opacity 0.4s ease;
}

.post-list-enter-from,
.post-list-leave-to {
  opacity: 0;
}
.post-list-move {
  transition: transform 0.4s ease;
}
</style>
