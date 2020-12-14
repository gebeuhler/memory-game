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
          >
            <v-img v-if="card.flipped" :src="card.src"></v-img>
            {{ card.id }}
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
      cards: [
        {
          id: 1,
          value: 1,
          flipped: false,
          src: "https://picsum.photos/id/1/120",
        },
        {
          id: 2,
          value: 1,
          flipped: false,
          src: "https://picsum.photos/id/1/120",
        },
        {
          id: 3,
          value: 2,
          flipped: false,
          src: "https://picsum.photos/id/50/120",
        },
        {
          id: 4,
          value: 2,
          flipped: false,
          src: "https://picsum.photos/id/50/120",
        },
        {
          id: 5,
          value: 3,
          flipped: false,
          src: "https://picsum.photos/id/100/120",
        },
        {
          id: 6,
          value: 3,
          flipped: false,
          src: "https://picsum.photos/id/100/120",
        },
        {
          id: 7,
          value: 4,
          flipped: false,
          src: "https://picsum.photos/id/150/120",
        },
        {
          id: 8,
          value: 4,
          flipped: false,
          src: "https://picsum.photos/id/150/120",
        },
        {
          id: 9,
          value: 5,
          flipped: false,
          src: "https://picsum.photos/id/200/120",
        },
        {
          id: 10,
          value: 5,
          flipped: false,
          src: "https://picsum.photos/id/200/120",
        },
        {
          id: 11,
          value: 6,
          flipped: false,
          src: "https://picsum.photos/id/250/120",
        },
        {
          id: 12,
          value: 6,
          flipped: false,
          src: "https://picsum.photos/id/250/120",
        },
        {
          id: 13,
          value: 7,
          flipped: false,
          src: "https://picsum.photos/id/300/120",
        },
        {
          id: 14,
          value: 7,
          flipped: false,
          src: "https://picsum.photos/id/300/120",
        },
        {
          id: 15,
          value: 8,
          flipped: false,
          src: "https://picsum.photos/id/350/120",
        },
        {
          id: 16,
          value: 8,
          flipped: false,
          src: "https://picsum.photos/id/350/120",
        },
        {
          id: 17,
          value: 9,
          flipped: false,
          src: "https://picsum.photos/id/400/120",
        },
        {
          id: 18,
          value: 9,
          flipped: false,
          src: "https://picsum.photos/id/400/120",
        },
        {
          id: 19,
          value: 10,
          flipped: false,
          src: "https://picsum.photos/id/450/120",
        },
        {
          id: 20,
          value: 10,
          flipped: false,
          src: "https://picsum.photos/id/450/120",
        },
        {
          id: 21,
          value: 11,
          flipped: false,
          src: "https://picsum.photos/id/500/120",
        },
        {
          id: 22,
          value: 11,
          flipped: false,
          src: "https://picsum.photos/id/500/120",
        },
        {
          id: 23,
          value: 12,
          flipped: false,
          src: "https://picsum.photos/id/550/120",
        },
        {
          id: 24,
          value: 12,
          flipped: false,
          src: "https://picsum.photos/id/550/120",
        },
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
          setTimeout(
            () => (this.cards = this.cards.filter((card) => !card.flipped)),
            3000
          );
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
