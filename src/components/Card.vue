<style scoped>
  article {
    background: var(--white);
    display: grid;
  }

  h2 {
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
