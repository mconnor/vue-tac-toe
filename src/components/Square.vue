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
  data() {
    return {
      // privateState: { value: '' },
    };
  },
  methods: {
    handleClick() {
      this.$emit('onClick', this.index);
    },
  },
};
</script>

<style>
.square {
    background: #0ff;
    border: 1px solid #999;
    float: left;
    font-size: 24px;
    font-weight: bold;
    line-height: 34px;
    height: 34px;
    margin-right: -1px;
    margin-top: -1px;
    padding: 0;
    text-align: center;
    width: 34px;
}

.square:focus {
    outline: none;
}
</style>
