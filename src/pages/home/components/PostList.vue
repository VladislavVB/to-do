<template>
  <transition-group name="post">
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
            <my-button
              v-if="post.copmlitePost === false"
              @click="copmlitePost(post)"
              class="complite"
            >
              <img src="@/assets/ok.svg" alt="" />
            </my-button>
            <my-button v-else @click="closePost(post)" class="complite">
              <img src="@/assets/close.svg" alt="" />
            </my-button>
          </div>
          <my-button
            @click="$emit('remove', post)"
            style="background-color: #c15151"
          >
            <img src="@/assets/del.svg" alt="" />
          </my-button>
        </div>
      </div>
    </div>
  </transition-group>
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
    &:first-child {
      border-top-left-radius: 20px;
      border-top-right-radius: 20px;
    }
    &:last-child {
      border-bottom: 0px solid #c4c4c4;
      border-bottom-left-radius: 20px;
      border-bottom-right-radius: 20px;
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



.post-item {
  display: inline-block;
  margin-right: 10px;
}
.post-enter-active,
.post-leave-active {
  transition: all 0.5s ease;
}
.post-enter-from,
.post-leave-to {
  opacity: 0;
  transform: translateY(30px);
}
</style>
