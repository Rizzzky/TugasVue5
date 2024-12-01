<template>
  <div id="app">
    <CommentList />
  </div>
</template>

<script>
import CommentList from "./components/CommentList.vue";

export default {
  name: "App",
  components: { CommentList }
};
</script>
