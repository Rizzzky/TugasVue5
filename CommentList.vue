<template>
  <div>
    <h2>Comments</h2>
    <form @submit.prevent="addComment">
      <input
        v-model="newComment.username"
        placeholder="Your name"
        required
      />
      <textarea
        v-model="newComment.comment"
        placeholder="Your comment"
        required
      ></textarea>
      <button type="submit">Add Comment</button>
    </form>

    <CommentItem
      v-for="(comment, index) in comments"
      :key="index"
      :username="comment.username"
      :comment="comment.comment"
      :date="comment.date"
    />
  </div>
</template>

<script>
import CommentItem from "./CommentItem.vue";

export default {
  name: "CommentList",
  components: { CommentItem },
  data() {
    return {
      newComment: {
        username: "",
        comment: ""
      },
      comments: []
    };
  },
  methods: {
    addComment() {
      if (this.newComment.username && this.newComment.comment) {
        const newEntry = {
          username: this.newComment.username,
          comment: this.newComment.comment,
          date: new Date().toISOString()
        };
        this.comments.push(newEntry);
        this.newComment.username = "";
        this.newComment.comment = "";
      }
    }
  }
};
</script>

<style scoped>
form {
  margin-bottom: 20px;
}
form input,
form textarea {
  display: block;
  width: 100%;
  margin-bottom: 10px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
form button {
  padding: 10px 20px;
  background-color: #007BFF;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
form button:hover {
  background-color: #0056b3;
}
</style>
