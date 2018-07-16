<style scoped>
  article {
    background: var(--gray);
    display: grid;
    justify-content: center;
  }

  h2 {
    background: var(--white);
    margin: 0;
    padding: var(--space);
  }
</style>
<template>
  <article>
    <h2>{{ title }}</h2>
    <img :src="image" :alt="title" />
  </article>
</template>

<script>
export default ({
  name: 'Card',
  props: ['title', 'image']
})
</script>
