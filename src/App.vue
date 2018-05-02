<template>
  <div id="app">
    <div class="videoContent">
      <barRageText :commentList="commentText"/>
      <barRageInput @commentText="getCommentText"/>
    </div>
    <div class="commentContent">
      <CommentList :commentList="commentText" />
    </div>
  </div>
</template>

<script>
import barRageText from './components/BarrageText'
import barRageInput from './components/BarRageInput'
import CommentList from './components/CommentList'
export default {
  name: 'App',
  components: {
    barRageText,
    barRageInput,
    CommentList
  },
  data () {
    return {
      commentText: []
    }
  },
  methods: {
    getCommentText: function (value) {
      this.commentText.push(value)
    }
  }
}
</script>

<style lang="scss">
  *{
    padding:0;
    margin:0;
  }
#app {
  font-family: 'PingFang SC', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  flex-direction: row;
  width:100vw;
  height:100vh;
  .videoContent{
    flex-grow:1;
    padding:5px 0;
    position: relative;
  }
  .commentContent{
    width:30%;
    padding:5px 0;
    padding-left: 10px;
    border-left:1px solid #ccc;
  }
}
</style>
