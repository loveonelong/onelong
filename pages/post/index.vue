<template lang="pug">
div.page-posts
  div.page-posts__wrap
    div
      input#posts-search
      label(for='posts-search') 搜索
    ul
      li 默认
      li 分类
      li 标签
    ul.post-list
      li(v-for='post in posts')
        nuxt-link(:to='getPostLink(post.id)')
          div.post
            h2 {{post.name}}
</template>

<script>
import getPosts from '~/helper/getPosts'

export default {
  name: '',
  components: {},
  mixins: {},
  props: {},
  data() {
    return {}
  },
  computed: {},
  watch: {},
  asyncData() {
    return {
      posts: getPosts()
    }
  },
  created() {},
  mounted() {},
  methods: {
    getPostLink(postId) {
      return `post/${this.posts[postId].path}`
    }
  }
}
</script>

<style lang="scss">
.page-posts {
  &__wrap {
    margin: 30px 60px;
  }
  .post-list {
    margin-top: 30px;
    li {
      display: block;

      margin-top: 20px;
      padding: 20px 16px;

      border-radius: 4px;
      box-shadow: 2px 2px 6px #f2f2f2;
      cursor: pointer;

      transition: transform 0.2s ease-in-out;
      &:hover {
        background: #fafafa;
        transform: scaleY(1.15) scaleX(1.05);
      }
      > a {
        display: block;

        height: 100%;
      }
      h2 {
        font-weight: 500;
      }
    }
  }
}
</style>
