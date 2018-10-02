<template id="">
  <div id='movie-list'>
    <div v-for='movie in filteredMovies' class='movie'>
      {{movie.title}}
    </div>
  </div>
</template>

<script type="text/javascript">
  import genres from '../util/genres';
  export default {
    data: function() {
      return {
        movies: [
          {title:'Kill Bill',genre:genres.CRIME},
          {title:'Home Alone',genre:genres.COMEDY},
          {title:'Auston Powers',genre:genres.COMEDY}
        ]
      }
    },
    props: ['genre', 'time'],
    methods: {
      moviePassesGenreFilter(movie) {
        if (!this.genre.length) return true;
        else return this.genre.find(genre => movie.genre === genre);
      }
    },
    computed: {
      filteredMovies() {
        return this.movies.filter(this.moviePassesGenreFilter);
      }
    }
  }
</script>
