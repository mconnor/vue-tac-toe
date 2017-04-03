<template>
  <div>

        <div  class="board">
          <div>{{status}}</div>
          <div class="board-row">
            <square :value=privateState.squares[0] v-on:onClick="onHandleClick(0)"></square>
            <square :value=privateState.squares[1] v-on:onClick="onHandleClick(1)"></square>
            <square :value=privateState.squares[2] v-on:onClick="onHandleClick(2)"></square>
          </div>
          <div class="board-row">
            <square :value=privateState.squares[3] v-on:onClick="onHandleClick(3)"></square>
            <square :value=privateState.squares[4] v-on:onClick="onHandleClick(4)"></square>
            <square :value=privateState.squares[5] v-on:onClick="onHandleClick(5)"></square>
          </div>
          <div class="board-row">
            <square :value=privateState.squares[6] v-on:onClick="onHandleClick(6)"></square>
            <square :value=privateState.squares[7] v-on:onClick="onHandleClick(7)"></square>
            <square :value=privateState.squares[8] v-on:onClick="onHandleClick(8)"></square>
          </div>
        </div>

      </div>
</template>

<script>
import Square from './Square';

export default {
  name: 'board',
  props: ['boardState'],
  components: {
    Square,
  },
  data() {
    return {
      status: 'play',
      privateState: Object.assign({}, this.boardState),
      //sharedState: this.boardState,
    };
  },
  methods: {
    onHandleClick(i) {
      const squares = this.privateState.squares.slice();
      if (squares[i] !== null) return;
      squares[i] = this.privateState.xIsNext ? 'X' : '0';

      this.privateState.squares = squares;
      this.privateState.xIsNext = !this.privateState.xIsNext;
      this.status = `Next player: ${this.privateState.xIsNext ? 'X' : 'O'}`;
      // this.boardState = this.privateState;
      this.$emit('onClick');
    },
  },
};

</script>

<style lang="css">

.board {
  display: flex;
  flex-direction: column;
  align-items: center;
}



</style>
