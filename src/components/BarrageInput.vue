<template>
  <div id="barrageInput">
    <input type="text" placeholder="请输入文字" v-model="inputValue" @keyup.enter="setValue()">
  </div>
</template>

<script>

export default {
  name: 'BarrageInput',
  data () {
    return {
      inputValue: ''
    }
  },
  methods: {
    setValue: function () {
      if (this.inputValue !== '') {
        this.$emit('commentText', this.inputValue)
      }
      this.inputValue = ''
    }
  }
}
</script>

<style lang="scss">
  #barrageInput{
    position: absolute;
    width:100%;
    bottom:20px;
    text-align: center;
    input{
      width:90%;
      border:1px solid #ccc;
      padding:10px;
      outline:none;
      border-radius: 5px;
      font-size: 24px;
    }
  }
</style>
