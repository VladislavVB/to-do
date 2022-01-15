<template>
  <form @submit.prevent class="home__form">
    <input
      v-model="post.title"
      class="case__input"
      type="text"
      placeholder="Описание дела..."
    />
    <button
      @click="createPost()"
      :class="{ active: this.post.title === '' }"
      class="btn case__add"
    >
      Добавить
    </button>
  </form>
</template>
<script>
export default {
  data() {
    return {
      post: {
        id: null,
        title: "",
        copmlitePost: false,
      },
    };
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit("create", this.post);
      this.post = {
        title: "",
        copmlitePost: false,
      };
    },
  },
};
</script>
<style lang="scss" scoped>
.case {
  &__add {
    width: 140px;
    height: 40px;
    background: #7d83b9;
    border-radius: 20px;
    color: #fff;
    border: none;
    cursor: pointer;
    &.active {
      opacity: 0.5;
      pointer-events: none;
    }
  }
  &__input {
    padding: 0 20px;
    width: 650px;
    background: #ffffff;
    border: 1px solid #c4c4c4;
    box-shadow: inset 0px 0px 10px 1px rgba(0, 0, 0, 0.25);
    border-radius: 20px;
  }
}
</style>
