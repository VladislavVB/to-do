<template>
  <div class="home">
    <div class="container">
      <!-- ss  -->
      <PostForm @create="createPost" />
      <div v-if="this.posts.length > 0" class="home__cases">
        <PostList :posts="posts" @remove="removePost" />
      </div>
      <h4 class="cases__zero" v-else>Дел нет :)</h4>
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
      posts: [],
    };
  },
  mounted() {
     this.posts = JSON.parse(localStorage.getItem('case'))
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      localStorage.setItem('case', JSON.stringify(this.posts))
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
      localStorage.setItem('case', JSON.stringify(this.posts))
    },
  },
  
};
</script>

<style lang="scss" scoped>
.cases {
  &__zero {
    text-align: center;
    margin-top: 40px;
    font-size: 20px;
    font-weight: 500;
    color: #fff;
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
  &__cases {
    border-radius: 20px;
    width: 100%;
    overflow: hidden;
    margin-top: 40px;
  }
}
</style>
