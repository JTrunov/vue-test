<template>
  <form @submit.prevent>
    <h4>Новый пост</h4>
    <my-input
      v-model="post.title"
      type="text"
      class="input"
      placeholder="Название"
    />
    <my-input
      v-model="post.body"
      type="text"
      class="input"
      placeholder="Описание"
    />
    <my-button
      style="align-self: flex-end; margin-top: 15px"
      class="btn"
      @click="createPost"
      >Создать пост</my-button
    >
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit("create", this.post);
      this.post = {
        title: "",
        body: "",
      };
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}
</style>
