<template>
  <div class="home">
    <div class="container">
      <!-- ss  -->
      <PostForm @create="createPost" />
      <div v-if="this.posts.length > 0" class="home__posts">
        <PostList :posts="posts" @remove="removePost" />
      </div>
      <h4 class="tasks__zero" v-else>Дел нет :)</h4>
    </div>
  </div>
</template>

<script>
import PostForm from "./components/PostForm";
import PostList from "./components/PostList";

export default {
  name: "Home",
  components: {
    PostForm,
    PostList,
  },
  data() {
    return {
      posts: [
        { id: 1, title: "Дело 1", copmlitePost: false },
        { id: 2, title: "Дело 2", copmlitePost: false },
        { id: 3, title: "Дело 3", copmlitePost: false },
      ],
    };
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
  },
};
</script>

<style lang="scss" scoped>
.tasks {
  &__zero {
    text-align: center;
    margin-top: 40px;
    font-size: 20px;
  }
}
.home {
  background-color: #a8d7da;
  min-height: 100vh;
  &__form {
    display: flex;
    padding-top: 50px;
    justify-content: space-between;
  }
  &__posts {
    border-radius: 20px;
    width: 100%;
    overflow: hidden;
    margin-top: 40px;
  }
  &__post {
    background-color: #fff;
    padding: 5px 20px;
    border-bottom: 1px solid #c4c4c4;
    color: #000;
    transition: 0.5s;
    &:last-child {
      border-bottom: 0px solid #c4c4c4;
    }
    &-head {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    &-btns {
      display: flex;
      button {
        border-radius: 50%;
        border: none;
        width: 30px;
        height: 30px;
        display: flex;
        justify-content: center;
        align-items: center;
        cursor: pointer;
      }
    }
  }
}
</style>
