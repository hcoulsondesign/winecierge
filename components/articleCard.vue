<template>
  <article class="card p-3 m-3">
    <img :src="article.urlToImage" :alt="article.title" class="card__img img-fluid mb-4">
    <h5 class="card__title">{{ article.title }}</h5>
    <!-- <p class="card__author">{{ article.name }}</p> -->
    <p class="card__descriptor text-left">{{ article.description }} <a href="article.url">Read more at <span class="font-italic">{{ article.sourceName }}</span></a></p>
  </article>
</template>

<script>
export default {
  props: {
    article: Object
  }
}
</script>
