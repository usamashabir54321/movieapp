<template>
	<div id="movie-grid" class="movies-grid">
		<div v-for="(movie, index) in movies" :key="index" class="movie">
			<div class="movie-img">
				<figure>
				    <img :src="`https://image.tmdb.org/t/p/w500/${movie.poster_path}`" alt="No Image In Nextlogixs" />
				    <figcaption>Nextlogixs {{ movie.title.slice(0, 25)}}</figcaption>
				</figure>
				<p class="review">{{ movie.vote_average }}</p>
				<p class="overview">{{ movie.overview }}</p>
			</div>
			<div class="info">
				<p class="title">{{ movie.title.slice(0, 25)}}<span v-if="movie.title.length > 25">...</span></p>
				<p class="release">Released:
					{{
						new Date(movie.release_date).toLocaleString('en-us', {
							month: 'long',
							day: 'numeric',
							year: 'numeric',
						})
					}}
				</p>
				<NuxtLink class="button button-light" :to="{ name: 'movies-movieid', params: { movieid: movie.id } }">
					Get More Info
				</NuxtLink>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		props: ['movies'],
	}
</script>
