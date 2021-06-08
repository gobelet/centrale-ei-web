<template>
  <div>
    <img
      alt="movie poster"
      :src="'https://image.tmdb.org/t/p/w400' + movie.poster_path"
    />
    <p>{{ movie.title }}</p>
    <p>Note moyenne : {{ movie.vote_average }}</p>
    <p>{{ movie.release_date }}</p>
  </div>
</template>

<script>
export default {
  name: "Movie",
  props: {
    movie: Array,
  },
};
</script>

<style scoped>
table {
  border-collapse: collapse;
}

th,
td {
  border: 1px solid #000000;
  padding: 10px;
}
</style>
