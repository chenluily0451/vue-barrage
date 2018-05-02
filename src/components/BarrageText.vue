<template>
  <div id="barrage">
    <div class="barrageLine">
      <span class="moveBlock">弹幕大军即将到来。。。</span>
    </div>
    <div class="barrageLine">
      <span class="moveBlock">弹幕大军即将到来。。。</span>
    </div>
    <div class="barrageLine">
      <span class="moveBlock">弹幕大军即将到来。。。</span>
    </div>
    <div class="barrageLine">
      <span class="moveBlock">弹幕大军即将到来。。。</span>
    </div>
    <div class="barrageLine">
      <span class="moveBlock">弹幕大军即将到来。。。</span>
    </div>
    <div class="barrageLine">
      <span class="moveBlock">弹幕大军即将到来。。。</span>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Barrage',
  props: ['commentList'],
  data () {
    return {
      commentArray: []
    }
  },
  watch: {
    'commentList': function () {
      this.commentArray = this.commentList
      this.getRandom()
    }
  },
  methods: {
    getRandom: function () {
      let barrageLine = document.querySelectorAll('.barrageLine')
      let randomNum = Math.round(Math.random() * barrageLine.length)
      this.createNode(randomNum)
    },
    createNode (index) {
      let newNode = document.createElement('span')
      newNode.setAttribute('class', 'moveBlock')
      newNode.innerHTML = this.commentArray[this.commentArray.length - 1]
      document.querySelectorAll('.barrageLine')[index].appendChild(newNode)
    }
  }
}
</script>å

<style lang="scss">
  #barrage{
    .barrageLine{
      padding:10px 0;
      position: relative;
      overflow: hidden;
      text-align: left;
      .moveBlock{
        display: inline-block;
        transform: translateX(-100vw);
        animation: barrageMove 5s linear;
      }
    }
  }
  @keyframes barrageMove
  {
    from {
      transform: translateX(100vw);
    }
    to {
      transform: translateX(-100%);
    }
  }
</style>
