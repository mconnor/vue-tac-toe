<template>
  <div className="game">
    <div className="game-info">
      <div>{{msg}}</div>
    </div>
       <div className="game-board">
         <board :board-state=store.state></board>
       </div>

     </div>
</template>
<script>
import Board from './Board';

export default {
  name: 'game',
  components: {
    Board,
  },

  data() {
    return {
      msg: 'Game',
      store: {
        state: {
          history: [{
            squares: Array(9).fill(null),
          }],
          squares: Array(9).fill(null),
          stepNumber: 0,
          xIsNext: true,
        },
      },
    };
  },
  methods: {
    onHandleClick() {
      const squares = this.boardState.squares.slice();
      this.store.state.squares = squares;
      // this.boardState.xIsNext = !this.boardState.xIsNext;
      // this.status = `Next player: ${this.boardState.xIsNext ? 'X' : 'O'}`;
      // this.state = this.boardState;
    },
  },
};
</script>
<style>

body {
  font: 14px "Century Gothic", Futura, sans-serif;
  margin: 20px;
}


.game {
  display: flex;
  flex-direction: row;
}

.game-info {
  margin-left: 20px;
}
</style>
