<template>
  <div class="board">
    <table class="sudoku-board">
      <tr v-for="(row, rownum) in board" :key=row>
        <td class="cell" v-for="(square, colnum) in row" :key="square">
          <SudokuSquare 
           @mousedown="focus[1] = rownum; focus[0] = colnum"
           :number="square" :row="rownum" :column="colnum" 
           :focus="rownum === focus[1] && colnum === focus[0]"/>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
import SudokuSquare from './SudokuSquare.vue'
export default {
  name: 'SudokuBoard',
  data: function() {
    let width = 9;
    let height = 9;
    let board = [];
    for(let a = 0; a < height; a++) {
      board.push([])
      for(let b = 0; b < width; b++) {
        board[a].push(0);
      }
    }
    return {
      board: board,
      width: width,
      height: height,
      focus: [3,0],
    }
  },
  components: {
    SudokuSquare,
  },
  methods: {
    handleInput(event) {
      console.log(event.target);
      console.log(this.board);
      if(/^[123456789]$/.test(event.key)) {
        this.board[this.focus[1]][this.focus[0]] = parseInt(event.key);
      }
    }
  },
  mounted() {
    document.body.addEventListener('keydown', (e) => {
      this.handleInput(e);
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .board {
    width: 100%;
  }
  table {
    height: 450px;
    width: 450px;
    border-collapse: collapse;
    margin: auto;
  }
  table tr:nth-of-type(3n) td {
    border-bottom: 3px black solid;
  }
  table tr:nth-of-type(3n+1) td {
    border-top: 3px black solid;
  }
  table tr td:nth-of-type(3n) {
    border-right: 3px black solid;
  }
  table tr td:nth-of-type(3n+1) {
    border-left: 3px black solid;
  }
  .cell {
    border: 0.5px black solid;
    vertical-align: middle;
    padding: 0;
  }
</style>
