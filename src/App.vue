<script>
import Card from './components/Card.vue'

export default {
  components: {
    Card,
  },
  mounted() {
    this.lastVisibleRow = this.grid.length - 1;
    setTimeout(() => {
      this.flipRow(this.grid.length - 1);
    }, 100); 
  },
  methods: {
    flipRow(row) {
       for (var cell in this.grid[0]) {
        this.flip(row, cell);
      }
    },
    flip(x, y) {
      this.grid[x][y].flipped = !this.grid[x][y].flipped;
    },
    fadeOut(x, y) {
      this.grid[x][y].visible = false;
    },
    async selectCard(x, y) {
      console.log(x, y);
      if (x != this.lastVisibleRow) {
          return; 
      }

      if (!this.locked) {
        this.locked = true;

        for (var row in this.grid) {
          this.fadeOut(row, y);
        }

        await new Promise(r => setTimeout(r, 500));
  
        for (var card in this.grid[this.lastVisibleRow]) {
          this.fadeOut(this.lastVisibleRow, card);
        }
        this.lastVisibleRow--;
        await new Promise(r => setTimeout(r, 500));
 
        this.flipRow(this.lastVisibleRow);
      }
      this.locked = false;
    },
  },
  data() {
    return {
      lastVisibleRow: 0,
      locked: false,
      grid: [
        [
          {'flipped': false, 'visible': true, 'cardType':1},
          {'flipped': false, 'visible': true, 'cardType':1},
          {'flipped': false, 'visible': true, 'cardType':1},
          {'flipped': false, 'visible': true, 'cardType':1},
          {'flipped': false, 'visible': true, 'cardType':1},
        ],
        [
          {'flipped': false, 'visible': true, 'cardType':2},
          {'flipped': false, 'visible': true, 'cardType':2},
          {'flipped': false, 'visible': true, 'cardType':2},
          {'flipped': false, 'visible': true, 'cardType':2},
          {'flipped': false, 'visible': true, 'cardType':2},
        ],
        [
          {'flipped': false, 'visible': true, 'cardType':3},
          {'flipped': false, 'visible': true},
          {'flipped': false, 'visible': true},
          {'flipped': false, 'visible': true},
          {'flipped': false, 'visible': true},
        ],
        [
          {'flipped': false, 'visible': true},
          {'flipped': false, 'visible': true},
          {'flipped': false, 'visible': true},
          {'flipped': false, 'visible': true},
          {'flipped': false, 'visible': true},
        ],
        [
          {'flipped': false, 'visible': true},
          {'flipped': false, 'visible': true},
          {'flipped': false, 'visible': true},
          {'flipped': false, 'visible': true},
          {'flipped': false, 'visible': true, 'cardType': 2},
        ],
        
      ]
    };
  },
};
</script>

<template>
  <div class="grid">
    <div v-for="(row, x) in grid" class="row">
      <div v-for="(cell, y) in row" class="column">
        <card :isFlipped="cell.flipped" 
              :isVisible="cell.visible"
              :frontLabel="cell.frontLabel"
              :cardType="cell.cardType"
              @click="selectCard(x, y)">
          <template v-slot:back>
            <!-- put your shitty back code here -->
            <p>back</p>
          </template>
        </card>
      </div>
    </div>
  </div>
</template>

<style>
.grid {
  display: flex;
  flex-direction: column;
}

.row {
  display: flex;
}

.column {
  flex: 1;
}
</style>

