<style>
  :root {
    --space: 1.25rem;
    --half-space: calc(var(--space) / 2);
    --section-height: 40vh;
    --radius: 3px;
    --black: hsl(0, 0%, 26%);
    --white: hsl(0, 0%, 96%);
    --gray: hsl(0, 0%, 80%);
  }

  *,
  *::before,
  *::after {
    box-sizing: border-box;
  }

  body {
    background: var(--white);
    color: var(--black);
  }

  html,
  body,
  #app {
    min-height: 100%;
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
    background: var(--gray);
    justify-content: center;
    align-items: center;
  }

  li {
    z-index: 0;
    visibility: hidden;
    grid-area: 1 / 1 / 2 / 2;
  }

  .visible {
    z-index: 1;
    visibility: visible;
    animation: slide-in 1s ease-out;
  }

  button {
    background: var(--black);
    color: var(--white);
    border: none;
    border-radius: var(--radius);
    padding: var(--half-space) var(--space);
    margin: var(--space) auto;
    display: block;
  }

  @keyframes slide-in {
    from {
      opacity: 0;
      transform: translateX(100%);
    },
    to {
      opacity: 1;
      transform: none;
    }
  }
</style>

<template>
  <div id="app">
    <header>
      <h1>Flashcards</h1>
    </header>

    <main>
      <transition-group name="fade" tag="ul">
        <li v-for="(card, index) in cards" :key="index" :class="{ visible: isCurrent(index) }">
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
    },
    isCurrent(index) {
      return index === this.current
    }
  }
}
</script>

<style>
</style>
