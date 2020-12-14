<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-toolbar-title class="mr-7">Memory Game</v-toolbar-title>
    </v-app-bar>

    <v-main>
      <v-container fluid>
        <div v-for="card in cards" :key="card.id" @click="flipCard(card)">
          <div v-if="card.flipped">value: {{ card.value }}</div>
          <div v-else>id: {{ card.id }}</div>
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
      cards: [
        { id: 1, value: 1, flipped: false },
        { id: 2, value: 1, flipped: false },
        { id: 3, value: 2, flipped: false },
        { id: 4, value: 2, flipped: false },
        { id: 5, value: 3, flipped: false },
        { id: 6, value: 3, flipped: false },
        { id: 7, value: 4, flipped: false },
        { id: 8, value: 4, flipped: false },
        { id: 9, value: 5, flipped: false },
        { id: 10, value: 5, flipped: false },
        { id: 11, value: 6, flipped: false },
        { id: 12, value: 6, flipped: false },
        { id: 13, value: 7, flipped: false },
        { id: 14, value: 7, flipped: false },
        { id: 15, value: 8, flipped: false },
        { id: 16, value: 8, flipped: false },
        { id: 17, value: 9, flipped: false },
        { id: 18, value: 9, flipped: false },
        { id: 19, value: 10, flipped: false },
        { id: 20, value: 10, flipped: false },
        { id: 21, value: 11, flipped: false },
        { id: 22, value: 11, flipped: false },
        { id: 23, value: 12, flipped: false },
        { id: 24, value: 12, flipped: false },
      ],
    };
  },
  created() {
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
        if (flippedCards[0].value === flippedCards[1].value) {
          alert("yay!");
          this.cards = this.cards.filter((card) => !card.flipped);
        } else {
          setTimeout(() => {
            flippedCards[0].flipped = false;
            flippedCards[1].flipped = false;
          }, 1000);
        }
      }
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
