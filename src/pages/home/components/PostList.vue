<template>
  <div
    v-for="post in posts"
    :key="post.id"
    :class="{ active: post.copmlitePost }"
    class="home__case"
  >
    <div class="home__case-head">
      <div class="home__case-title">{{ post.title }}</div>
      <div class="home__case-btns">
        <div class="okey__btns">
          <button
            v-if="post.copmlitePost === false"
            @click="copmlitePost(post)"
            class="complite"
          >
            <img src="@/assets/ok.svg" alt="" />
          </button>
          <button v-else @click="closePost(post)" class="complite">
            <img src="@/assets/close.svg" alt="" />
          </button>
        </div>
        <button @click="$emit('remove', post)" class="remove">
          <img src="@/assets/del.svg" alt="" />
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    posts: {
      type: Array,
    },
  },
  data() {
    return {
      postActive: false,
    };
  },
  methods: {
    copmlitePost(post) {
      post.copmlitePost = true;
      console.log(this.posts);
      localStorage.setItem("case", JSON.stringify(this.posts));
    },
    closePost(post) {
      post.copmlitePost = false;
      localStorage.setItem("case", JSON.stringify(this.posts));
    },
  },
};
</script>

<style lang="scss" scoped>
.home {
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
  &__case {
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
    &.active {
      background-color: #d8f4f5;
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
        margin-left: 10px;
      }
    }
  }
}
.complite {
  background-color: #71a663;
}
.remove {
  background-color: #c15151;
}
</style>
