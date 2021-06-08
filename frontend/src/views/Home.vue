<template>
  <div class="home">
    <h1>Liste des films</h1>
    <p>
      For a guide and recipes on how to configure / customize this project,<br />
      check out the
      <a href="https://cli.vuejs.org" target="_blank">vue-cli documentation</a>.
    </p>

    <div class="user-input">
      <input v-model="movieName" />
    </div>

    <div class="movie-table">
      <p v-for="movie in movies" :key="movie.id">
        <div class="movie-seule">
          <Movie :movie="movie" />
        </div>
      </p>
    </div>
  </div>
</template>

<script>
import Movie from "@/components/Movie.vue";
import axios from "axios";

export default {
  name: "Home",
  components: { Movie },
  data: function () {
    return {
      movieName: "",
      movies: [],
    };
  },
  methods: {
    fetchMovies: function () {
      axios
        .get(
          "https://api.themoviedb.org/3/movie/popular?api_key=a0a7e40dc8162ed7e37aa2fc97db5654&language=en-US&page=1"
        )
        .then((response) => {
          this.movies = response.data.results;
          console.log("ok");
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },

  created() {
    this.fetchMovies();
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.home {
  text-align: center;
}
.movie-seule {
  text-align: center;
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  justify-content: space-around;
}
.movie-table {
  text-align: center;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-around;
}

h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
