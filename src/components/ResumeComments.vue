<template>
  <div className="container">
    <p>
      <button className="btn primary" @click="loadComments" v-if="!visibleComments">Загрузить комментарии</button>
    </p>
    <div className="card" v-if="visibleComments">
      <h2>Комментарии</h2>
      <ul className="list">
        <resume-comment-item v-for="comment in comments" :key="comment.id">
          <template #email>
            {{comment.email}}
          </template>
          <template #body>
            {{comment.body}}
          </template>
        </resume-comment-item>
      </ul>
    </div>
    <div class="loader" v-if="isLoading"></div>
  </div>
</template>

<script>
import ResumeCommentItem from "./ResumeCommentItem";

export default {
  data() {
    return {
      isLoading: false,
      comments: []
    }
  },
  methods: {
    async loadComments() {
      this.isLoading = true
      this.comments = []
      let request = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42')
      this.comments = await request.json()
      this.isLoading = false
    }
  },
  computed: {
    visibleComments() {
      return this.comments.length > 0
    }
  },
  components: {
    ResumeCommentItem
  }
}
</script>

<style scoped>

</style>