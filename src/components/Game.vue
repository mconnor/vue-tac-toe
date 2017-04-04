<template>
<div className="game">
      <div className="game-info">
            <div>{{msg}}</div>
            <div>{{status}}</div>
      </div>
      <div className="game-board">i
          <board :store=store v-on:onClick="onGameHandleClick"></board>
      </div>
</div>
</template>
<script>
import Board from './Board';

function calculateWinner(squares) {
  const lines = [
    [0, 1, 2],
    [3, 4, 5],
    [6, 7, 8],
    [0, 3, 6],
    [1, 4, 7],
    [2, 5, 8],
    [0, 4, 8],
    [2, 4, 6],
  ];
  /* eslint no-plusplus: ["error", { "allowForLoopAfterthoughts": true }]*/
  for (let i = 0; i < lines.length; i++) {
    const [a, b, c] = lines[i];
    if (squares[a] && squares[a] === squares[b] && squares[a] === squares[c]) {
      return squares[a];
    }
  }
  return null;
}

export default {
  name: 'game',
  components: {
    Board,
  },
  // TODO history and check for winnner
  data() {
    return {
      msg: 'Vue-Tac-Toe',
      store: {
        state: {
          stepNumber: 0,
          xIsNext: true,
          squares: Array(9)
            .fill(null),
        },
      },
      status: 'play',
    };
  },
  methods: {
    onGameHandleClick: function onGameHandleClick(i) {
      const squares = this.store.state.squares.slice();
      if (calculateWinner(squares) || squares[i]) {
        /* eslint no-console: ["error", { allow: ["warn", "error"] }] */
        console.warn('winner');
        this.status = `${this.store.state.xIsNext ? 'O' : 'X'} is the winner`;
        return;
      }
      /* eslint no-console: ["error", { allow: ["warn", "error"] }] */
      console.warn('no winner yet');

      squares[i] = this.store.state.xIsNext ? 'X' : '0';
      this.store.state.squares = squares;
      this.store.state.xIsNext = !this.store.state.xIsNext;
      this.status = `Next player: ${this.store.state.xIsNext ? 'X' : 'O'}`;
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
