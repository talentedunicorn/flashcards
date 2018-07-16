<style>
  :root {
    --space: 1.25rem;
  }

  #app {
    min-height: 100%;
  }

  @supports (min-height: 100vh) {
    #app {
      min-height: 100vh;
    }
  }

  header {
    padding: var(--space);
  }

  header h1 {
    margin: 0;
  }

  ul {
    list-style: none;
    padding: 0;
    margin: 0;
    display: grid;
    background: orange;
    justify-content: center;
  }

  .slide-enter, .slide-leave-to {
    opacity: 0;
  }

  .slide-enter-active,
  .slide-leave-active {
    transition: all ease-in-out 1s;
  }
</style>

<template>
  <div id="app">
    <header>
      <h1>Flashcards</h1>
    </header>

    <main>
      <transition-group name="slide" tag="ul">
        <li v-for="(card, index) in cards" :key="index" v-show="current === index">
          <Card :title="card.title" :image="card.image" />
        </li>
      </transition-group>

      <button @click="changeCard">Click me</button>
    </main>
  </div>
</template>

<script>
import 'normalize.css'
import Card from './components/Card'

export default {
  name: 'app',
  components: {
    Card
  },
  data () {
    return {
      current: 0,
      cards: [
        { title: "Monday", image: "//picsum.photos/300/200" },
        { title: "Tuesday", image: "//picsum.photos/400/200" },
        { title: "Wednesday", image: "//picsum.photos/500/300" }
      ]
    }
  },
  methods: {
    changeCard() {
      console.log('Changing card', this.current)
      if (this.current < this.cards.length - 1) {
        this.current++
      } else {
        this.current = 0
      }

    }
  }
}
</script>

<style>
</style>
