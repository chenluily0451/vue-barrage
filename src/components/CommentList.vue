<template>
  <div id="CommentList">
    <ul>
      <li v-for="(i, index) in commentArray" :key="index"><span class="user">匿名用户：</span><span class="userComments">{{ i }}</span></li>
      <li v-if="commentArray.length ==0">暂无数据</li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'BarrageInput',
  props: ['commentList'],
  data () {
    return {
      commentArray: []
    }
  },
  watch: {
    'commentList': function () {
      this.commentArray = this.commentList
    }
  }
}
</script>

<style lang="scss">
  #CommentList{
    height:98vh;
    overflow-y: auto;
    font-size: 20px;
    ul{
      li{
        word-break: break-all;
        margin-bottom: 25px;
        padding: 0 15px;
        color: #666;
        display: flex;
        flex-direction: row;
        .user{
          flex-shrink: 0;
        }
        .userComments{
          color: #999;
        }
      }
    }
  }
</style>
