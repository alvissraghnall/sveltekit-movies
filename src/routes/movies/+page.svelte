<script lang="ts">
    import Carousel from "../../components/MovieCarousel.svelte";
    import { movies as moviesStore } from "../../store/movies";
	import MovieCard from '../../components/MovieCard.svelte';
    import type { Movie } from "../../types/Movies";    
    import type {PageData} from './$types';

    const imagePath = "https://image.tmdb.org/t/p/w500/";
    let movies: Movie[];
    export let data;

    movies = data.results;
    console.log(movies);
    
    moviesStore.set(movies);
</script>

<Carousel data={$moviesStore} />

<h2> popular </h2>
<div id="popular" class="movies">
    {#each $moviesStore as movie}
        <MovieCard title={movie.title} poster_path={movie.poster_path ? movie?.poster_path : ""} imagesLink={imagePath} />
    {/each}
</div>

<style>
    .movies {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        background-image: linear-gradient(to bottom left, #1f2937, #111827);
		background-attachment: fixed;
        width: 100%;
    }

    h2 {
        text-transform: uppercase;
        font-size: 2.3rem;
        margin: 2.5rem;
        font-weight: 900;
        font-family: monospace, sans-serif, serif;
    }
</style>