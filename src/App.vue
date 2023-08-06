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
    hideEntryText() {
      this.showEntryText = false;
    },
  },
  data() {
    return {
      showEntryText: true,
      entryText: "This is the entry text you want to display.",
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
          {'flipped': false, 'visible': true, 'cardType':3, 'text':"at the bus stop - in\n first grade. You had\nbraids and he was\n missing front teeth.\n But it was love at \nfirst sight"},
          {'flipped': false, 'visible': true, 'cardType':3, 'text': 'when you played\n Juliet and he played\n Romeo. Was that \nfirst kiss just\n acting? The next \nones sure weren\'t'},
          {'flipped': false, 'visible': true, 'cardType':3, 'text': 'on summer vacation\nat the shoor. Aaggh.\nLong distance phone\n bills'},
          {'flipped': false, 'visible': true, 'cardType':3, 'text': 'in math class. He\n asked you for help\n with his homework\n and then you moved\n on to other subjects'},
          {'flipped': false, 'visible': true, 'cardType':3, 'text': 'when you were\n bored out of your\n mind at a wedding\nand he appeared\n out of nowhere\n and asked you\n to dance'},
        ],
        [
          {'flipped': false, 'visible': true, 'cardType':2, 'text':'his confidence.\nHe\'s not a follower\n - he\'s a leader'},
          {'flipped': false, 'visible': true, 'cardType':2, 'text': 'his strong faith.\n Never swaying, it\n guides his actions\n and the way he\n treats people'},
          {'flipped': false, 'visible': true, 'cardType':2, 'text':'his muscles. When he\nflexes his biceps you\nget weak in the knees'},
          {'flipped': false, 'visible': true, 'cardType':2, 'text': 'he\'s a great listener...\nWhen you\'re around\n him you\'re blushing\nbecause you realize\nyou\'ve told him\nEVERYTHING'},
          {'flipped': false, 'visible': true, 'cardType':2,  'text': 'his sense of humor.\n It\'s contagious. As in,\n no laugh-track\n needed'},
        ],
        [
          {'flipped': false, 'visible': true, 'cardType': 5, 'text': 'jumping up and\n down and cheering\n at a game on TV'},
          {'flipped': false, 'visible': true, 'cardType': 5, 'text':'barefooting off the\n beach with you\n driving the boat'},
          {'flipped': false, 'visible': true, 'cardType': 5, 'text': 'checking someone hard in a hockey\n game'},
          {'flipped': false, 'visible': true, 'cardType': 5, 'text': 'floating on his back\nafter touching first in\nthe 100m fly'},
          {'flipped': false, 'visible': true, 'cardType': 5,  'text': 'covered in mud after\na vicious mountain\nbike ride'},
        ],
        [
          {'flipped': false, 'visible': true, 'cardType':4, 'text': 'He may be a cutie,\nbut you need more\nthan just a pretty\nface'},
          {'flipped': false, 'visible': true, 'cardType':4, 'text': 'Suh -w-e-e-t!'},
          {'flipped': false, 'visible': true, 'cardType':4, 'text': 'OK, so when are you\ngoing to set us up\nwith his friends?!'},
          {'flipped': false, 'visible': true, 'cardType':4, 'text': 'Is his homepage\nwww.weirdo.com?'},
          {'flipped': false, 'visible': true, 'cardType':4, 'text': 'He gives us hope that\nnice, romantic guys\naren\'t just fictional\ncharacters'},
        ],
        
      ]
    };
  },
};
</script>

<template>
  <div>
    <div v-if="showEntryText" class="overlay-container">
      <div class="overlay-text">
        <p>{{ entryText }}</p>
        <button @click="hideEntryText">Ok</button>
      </div>
    </div>
  <div class="grid">
    <div v-for="(row, x) in grid" class="row">
      <div v-for="(cell, y) in row" class="column">
        <card :isFlipped="cell.flipped" 
              :isVisible="cell.visible"
              :frontLabel="cell.frontLabel"
              :cardType="cell.cardType"
              :cardText="cell.text"
              @click="selectCard(x, y)">
          <template v-slot:back>
            <!-- put your shitty back code here -->
            <p>back</p>
          </template>
        </card>
      </div>
    </div>
  </div>
  <a style="color:black; font-size:xx-small" href="https://www.flaticon.com/free-icons/spiral" title="spiral icons">Spiral icons created by Smashicons - Flaticon; </a>
  <a style="color:black; font-size:xx-small" href="https://www.flaticon.com/free-icons/spiral" title="spiral icons">Spiral icons created by BomSymbols - Flaticon; </a>
</div>
</template>

<style>
.grid {
  display: flex;
  flex-direction: column;
  /* background-color: #fa8128; */
}

.row {
  display: flex;
}

.column {
  flex: 1;
}

/* Styles for the main website content and other components */
.overlay-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7); /* Semi-transparent background */
  display: flex;
  justify-content: center;
  align-items: center;
  z-index:999;
}

.overlay-text {
  background-color: #fa8128; /* White background for the text box */
  padding: 20px;
  border-radius: 5px;
  text-align: center;
}
</style>

