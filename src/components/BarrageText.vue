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
      let colorArray = [
        '#9be86A',
        '#ff0000',
        '#3cb664',
        '#2792f2',
        '#000000',
        '#fecd52'
      ]
      let fontSizeArray = [
        '14px',
        '16px',
        '18px',
        '20px',
        '24px',
        '30px'
      ]
      if (randomNum >= 0 && randomNum < barrageLine.length) {
        this.createNode(randomNum, colorArray[randomNum], fontSizeArray[randomNum])
      }
    },
    createNode (index, color, fontsize) {
      let newNode = document.createElement('span')
      newNode.setAttribute('class', 'moveBlock')
      newNode.setAttribute('style', 'font-size:' + fontsize + ';' + 'color:' + color)
      newNode.innerHTML = this.commentArray[this.commentArray.length - 1]
      document.querySelectorAll('.barrageLine')[index].appendChild(newNode)
      this.deleteNode(index)
    },
    deleteNode (index) {
      let barrageNode = document.querySelectorAll('.barrageLine')[index]
      setTimeout(() => {
        barrageNode.removeChild(barrageNode.childNodes[0])
      }, 9000)
    }
  }
}
</script>

<style lang="scss">
  #barrage{
    .barrageLine{
      padding:10px 0;
      position: relative;
      overflow: hidden;
      text-align: left;
      .moveBlock{
        display: inline-block;
        animation: barrageMove 8s linear;
        white-space:nowrap;
      }
    }
  }
  @keyframes barrageMove
  {
    from {
      transform: translateX(100vw);
    }
    to {
      transform: translateX(-50vw);
    }
  }
</style>
