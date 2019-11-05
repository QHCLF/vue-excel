<template>
  <div id="app">
    <table class="sheet">
      <thead>
        <tr>
          <th v-for="item in column" :key="item" v-text="item.text"></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in rows" :key="item">
          <th 
          v-for="cell in item" :key="cell" 
          v-text="cell.text" 
          v-bind:contenteditable="cell.contentEditable"
          v-on:click="focus(cell)"
          v-on:blur="change"
          ></th>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: "app",
  data() {
    return {
      column: [
        { row: 0, col: 0, text: " " },
        { row: 0, col: 1, text: "A" },
        { row: 0, col: 2, text: "B" },
        { row: 0, col: 3, text: "C" },
        { row: 0, col: 4, text: "D" },
        { row: 0, col: 0, text: "E " }
      ],
      rows: [
        [
          { row: 1, col: 0, text: "1" , contentEditable: false},
          { row: 1, col: 1, text: " ", contentEditable: true},
          { row: 1, col: 2, text: " " , contentEditable: true},
          { row: 1, col: 3, text: " ", contentEditable: true },
          { row: 1, col: 4, text: " " , contentEditable: true},
          { row: 1, col: 5, text: " ", contentEditable: true }
        ],
        [
          { row: 2, col: 0, text: "2", contentEditable: false },
          { row: 2, col: 1, text: " ", contentEditable: true },
          { row: 2, col: 2, text: " ", contentEditable: true },
          { row: 2, col: 3, text: " ", contentEditable: true },
          { row: 2, col: 4, text: " " , contentEditable: true},
          { row: 2, col: 5, text: " ", contentEditable: true }
        ],
        [
          { row: 3, col: 0, text: "3", contentEditable: false },
          { row: 3, col: 1, text: " ", contentEditable: true },
          { row: 3, col: 2, text: " ", contentEditable: true },
          { row: 3, col: 3, text: " ", contentEditable: true },
          { row: 3, col: 4, text: " " , contentEditable: true},
          { row: 3, col: 5, text: " ", contentEditable: true }
        ],
        [
          { row: 4, col: 0, text: "4" },
          { row: 4, col: 1, text: " " , contentEditable: true},
          { row: 4, col: 2, text: " " , contentEditable: true},
          { row: 4, col: 3, text: " ", contentEditable: true },
          { row: 4, col: 4, text: " ", contentEditable: true },
          { row: 4, col: 5, text: " " , contentEditable: true}
        ],
        [
          { row: 5, col: 0, text: "5", contentEditable: false },
          { row: 5, col: 1, text: " ", contentEditable: true },
          { row: 5, col: 2, text: " ", contentEditable: true },
          { row: 5, col: 3, text: " ", contentEditable: true },
          { row: 5, col: 4, text: " ", contentEditable: true },
          { row: 5, col: 5, text: " " , contentEditable: true}
        ]
      ],
      curRow: 0,
      curCol: 0
    };
  },
  methods:{
    focus(cell){
      this.curRow = cell.row;
      this.curCol = cell.col;
    },
    change(e){
      let row = this.curRow, col = this.curCol, text= '';
        window.console.log(e);
      if(row > 0 && col > 0){
        text = e.target.innerText;
        this.rows[row - 1][col].text = text;
      }
    }
  },
  components: {}
};
</script>

<style lang="less" scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.sheet {
  width: 80%;
  margin-left: 10%;
  tr{
    width: 100%;
    display: flex;
    border-top: 2px solid grey;
    border-bottom: 2px solid grey;
  }
  th{
    height: 10vh;
    line-height: 10vh;
    font-size: 3vw;
    flex: 1;
    border-left: 2px solid grey;
    border-right: 2px solid grey;
  }
}
</style>
