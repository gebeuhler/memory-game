<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-toolbar-title class="mr-7">Memory Game</v-toolbar-title>
    </v-app-bar>

    <v-main>
      <v-container fluid>
        <div class="d-flex flex-wrap">
          <v-card
            v-for="card in cards"
            :key="card.id"
            @click="flipCard(card)"
            min-height="150"
            min-width="150"
            class="mr-4 mb-4"
            :disabled="!card.inPlay"
          >
            <v-img v-if="card.flipped || !card.inPlay" :src="card.src"></v-img>
          </v-card>
        </div>
      </v-container>
    </v-main>
    <v-footer color="primary" app>
      <span class="white--text"
        >George Beuhler &copy; {{ new Date().getFullYear() }}</span
      >
    </v-footer>
  </v-app>
</template>
<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      cards: [],
    };
  },
  created() {
    this.generateCards();
    this.cards = this.shuffle(this.cards);
  },
  computed: {
    flippedCards() {
      return this.cards.filter((card) => card.flipped);
    },
  },
  methods: {
    flipCard(card) {
      card.flipped = true;
      let flippedCards = this.flippedCards;
      if (flippedCards.length === 1) {
        return;
      } else if (flippedCards.length === 2) {
        if (flippedCards[0].src === flippedCards[1].src) {
          setTimeout(() => {
            flippedCards[0].inPlay = false;
            flippedCards[1].inPlay = false;
            flippedCards[0].flipped = false;
            flippedCards[1].flipped = false;
            if (this.cards.filter((card) => card.inPlay).length < 3) {
              alert("You win!");
            }
          }, 2000);
        } else {
          setTimeout(() => {
            flippedCards[0].flipped = false;
            flippedCards[1].flipped = false;
          }, 2000);
        }
      }
    },
    generateCards() {
      const ret = [];
      let src;
      const random = (min = 0, max = 50) => {
        let num = Math.random() * (max - min) + min;

        return Math.floor(num);
      };

      for (let i = 1; i < 25; i++) {
        if (i % 2 === 1) {
          src = `https://picsum.photos/id/${random(1, 1000)}/120`;
        }
        ret.push({
          id: i,
          flipped: false,
          inPlay: true,
          src,
        });
      }
      this.cards = ret;
    },
    shuffle(array) {
      // https://stackoverflow.com/questions/2450954/how-to-randomize-shuffle-a-javascript-array

      let currentIndex = array.length,
        temporaryValue,
        randomIndex;

      // While there remain elements to shuffle...
      while (0 !== currentIndex) {
        // Pick a remaining element...
        randomIndex = Math.floor(Math.random() * currentIndex);
        currentIndex -= 1;

        // And swap it with the current element.
        temporaryValue = array[currentIndex];
        array[currentIndex] = array[randomIndex];
        array[randomIndex] = temporaryValue;
      }

      return array;
    },
  },
};
</script>
