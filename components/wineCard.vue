<template>
  <!-- <article class="wineCard">
    <h2 class="card__vintage">{{ wine.vintage }}</h2>
    <h3 class="card__title">{{ wine.name }}</h3>
    <p class="card__score">{{ wine.score }}</p>
  </article> -->
  <article class="card">
    <img :src="country.flag" :alt="country.name" class="card__img">
    <h2 class="card__title">{{ country.name }}</h2>
    <p class="card__copy">{{ country.subregion }}</p>
  </article>
  <!-- <article class="card">
    <img :src="country.flag" :alt="country.name" class="card__img">
    <h2 class="card__title">{{ article.name }}</h2>
    <p class="card__author">{{ country.author }}</p>
  </article> -->
</template>

<script>
export default {
  props: {
    country: Object
  }
}
</script>

<!-- <style lang="scss">
.card {
	margin: 1rem;
	border: 1px solid #000;
	padding: 1.5rem;
	max-width: 200px;
	min-height: 200px;
	&__img {
		display: block;
		margin-bottom: 1rem;
	}
	&__title {
		font-size: 1rem;
		margin-bottom: .25rem;
	}
	&__copy {
		font-size: .875rem;
	}
}
</style> -->
