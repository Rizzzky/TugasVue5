<template>
  <div class="comment-item">
    <p><strong>{{ username }}</strong></p>
    <p>{{ comment }}</p>
    <small>{{ formattedDate }}</small>
  </div>
</template>

<script>
export default {
  name: "CommentItem",
  props: {
    username: {
      type: String,
      required: true
    },
    comment: {
      type: String,
      required: true
    },
    date: {
      type: String,
      required: true
    }
  },
  computed: {
    formattedDate() {
      const date = new Date(this.date);
      return date.toLocaleDateString() + " " + date.toLocaleTimeString();
    }
  }
};
</script>

<style scoped>
.comment-item {
  border: 1px solid #ddd;
  padding: 10px;
  margin-bottom: 10px;
  border-radius: 5px;
}
</style>
