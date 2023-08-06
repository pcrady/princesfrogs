<script>
import Card from './components/Card.vue'

export default {
  components: {
    Card,
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
    async finalMethod() {
      await new Promise(r => setTimeout(r, 1000));
      this.showYouFoundYourPrince = true;  
      await new Promise(r => setTimeout(r, 1000));
      this.showYouFoundYourPrince = false;
      await new Promise(r => setTimeout(r, 1000));
      this.showMaddie = true;  
      await new Promise(r => setTimeout(r, 1000));
      this.showHeart = true; 
      await new Promise(r => setTimeout(r, 1000));
      this.showCrowns = true; 
      await new Promise(r => setTimeout(r, 1000));
      this.showCongrats = true; 
      await new Promise(r => setTimeout(r, 1000));
      this.showDate = true; 
    },
    async selectCard(x, y) {
      if (this.lastVisibleRow === null) {
        this.lastVisibleRow = this.grid.length - 1;
        this.flipRow(this.lastVisibleRow);
        return;
      }

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
      if (this.lastVisibleRow === 0) {
        this.finalMethod();
      }
    },
    hideEntryText() {
      this.showEntryText = false;
    },
  },
  data() {
    return {
      showEntryText: true,
      lastVisibleRow: null,
      locked: false,
      showMaddie: false,
      showHeart: false, 
      showCrowns: false,
      showCongrats: false,
      showYouFoundYourPrince: false,
      showDate: false,
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
        <div>            
            <img src="./components/icons/princesfrogs-big.png" 
                 style=" 
                      position: relative; 
                      rotate: 0;
                      width: 400px;
                      left: 0px;"></div>
            <i class="fa-solid" 
               style="color: #ffb302; 
                      rotate: 0deg; 
                      position: relative; 
                      top: -249px; 
                      left: -100px;
                      text-shadow: -1px 0 black, 0 1px black, 1px 0 black, 0 -1px black; /* Create the outline */
                      font-size:3.5em;">&#xf521;
            </i>
            <p style="position:relative; top:-100px;">Find your Prince today!<br>Choose one guy to dump each round until you've got your guy. <br>Click on the first row to get started! </p>
        <button style="position:relative; top:-90px;" @click="hideEntryText">Ok</button>
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
    <Transition>
    <div v-if="showYouFoundYourPrince"
      style="
        position:absolute; 
        top:250px; 
        left:-120px;
        width: 300%;
        height: 100%s"
      class="fade-element">
          <p style="font-size:3em; 
          font-family: 'Times New Roman', Times, serif;
          font-weight: bold;
          color: #31b73e">You Found Your Prince!</p>
    </div>
  </Transition>
    <Transition>
    <div v-if="showMaddie"
      style="
        position:absolute; 
        top:-0px; 
        left:-150px;"
      class="fade-element">
          <card :isFlipped="true" 
                :isVisible="true"
                :cardType=6></card>
    </div>
  </Transition>
  <Transition>
    <div v-if="showHeart"
      style="
        position:absolute; 
        top:-150px; 
        left:-290px;"
      class="fade-element">
      <i class="fa-regular" 
               style="color: #4b006e; font-size:40em">&#xf004;
            </i>
    </div>
  </Transition>
  <Transition>
    <div v-if="showHeart"
      style="
        position:absolute; "
      class="fade-element">
      <i class="fa-solid" 
               style="color: #ffb302; 
                      rotate: 15deg; 
                      position: absolute; 
                      top: -30px; 
                      left: 29px;
                      text-shadow: -1px 0 black, 0 1px black, 1px 0 black, 0 -1px black; /* Create the outline */
                      font-size:7em;">&#xf521;
            </i>
            <i class="fa-solid" 
               style="color: #ffb302; 
                      rotate: -10deg; 
                      position: absolute; 
                      top: -20px; 
                      left: -110px;
                      text-shadow: -1px 0 black, 0 1px black, 1px 0 black, 0 -1px black; /* Create the outline */
                      font-size:7em;">&#xf521;
            </i>
    </div>
  </Transition>
  <Transition>
    <div v-if="showCongrats"
      style="
        position:absolute; 
        top:250px; 
        left:-325px;
        width: 400%;
        height: 100%s"
      class="fade-element">
          <p style="font-size:3em; 
          font-family: 'Times New Roman', Times, serif;
          font-weight: bold;
          text-align: center;
          color: #31b73e">Congratulations<br>Maddie and Colt!</p>
    </div>
  </Transition>
  <Transition>
    <div v-if="showDate"
      style="
        position:absolute; 
        top:-90px; 
        left:-330px;
        width: 400%;
        height: 100%s"
      class="fade-element">
          <p style="font-size:3em; 
          font-family: 'Times New Roman', Times, serif;
          font-weight: bold;
          text-align: center;
          color: #31b73e">October 7, 2023</p>
    </div>
  </Transition>
  </div>
  <a style="position: fixed; bottom: 10px; left: 0; color:lightgray; font-size:xx-small" href="https://www.flaticon.com/free-icons/spiral" title="spiral icons">Spiral icons created by Smashicons - Flaticon; </a>
  <a style="position: fixed; bottom: 0; left: 0; color:lightgray; font-size:xx-small" href="https://www.flaticon.com/free-icons/spiral" title="spiral icons">Spiral icons created by BomSymbols - Flaticon; </a>
</div>
</template>

<style>
.grid {
  display: flex;
  flex-direction: column;
  position: relative;
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
  width: 500px;
  height: 400px;
  text-align: center;
}

body {
  background-color: #f1e3a4;
}

.v-enter-active,
.v-leave-active {
  transition: opacity 1s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

</style>

