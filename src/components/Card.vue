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
