<template lang="html">
  <button class="square" v-on:click="handleClick">
       <span>{{value}}</span>
    </button>
</template>

<script>
export default {
  props: {
    index: Number,
    value: null,
    onClick: Function,
  },
  methods: {
    handleClick() {
      this.$emit('onClick', this.index);
    },
  },
};
</script>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css?family=Caveat+Brush');
$box-size: 68px;
$hopbush: #c69;

.square {
    font-family: 'Caveat Brush', cursive;
    color: white;
    background: $hopbush ;
    border: 2px solid #999;
    float: left;
    font-size: 48px;
    font-weight: bold;
    line-height: $box-size;
    height: $box-size;
    margin-right: -1px;
    margin-top: -1px;
    padding: 0;
    text-align: center;
    width: $box-size;
}

.square:focus {
    outline: none;
}
</style>
