<template>
    <b-autocomplete
      :data="data"
      placeholder="Busca un producto"
      field="title"
      :loading="isFetching"
      @typing="getAsyncData"
      @select="option => selected = option"
    >
      <template slot-scope="props">
        <div class="media">
          <div class="media-left">
            <img width="32" :src="`https://image.tmdb.org/t/p/w500/${props.option.poster_path}`" />
          </div>
          <div class="media-content">
            {{ props.option.title }}
            <br />
            <small>
              Released at {{ props.option.release_date }},
              rated
              <b>{{ props.option.vote_average }}</b>
            </small>
          </div>
        </div>
      </template>
    </b-autocomplete>
</template>

<script>
import debounce from "lodash/debounce";

export default {
  data() {
    return {
      data: [],
      selected: null,
      isFetching: false
    };
  },
  methods: {
    // You have to install and import debounce to use it,
    // it's not mandatory though.
    getAsyncData: debounce(function(name) {
      if (!name.length) {
        this.data = [];
        return;
      }
      this.isFetching = true;
      this.$http
        .get(
          `https://api.themoviedb.org/3/search/movie?api_key=bb6f51bef07465653c3e553d6ab161a8&query=${name}`
        )
        .then(({ data }) => {
          this.data = [];
          data.results.forEach(item => this.data.push(item));
        })
        .catch(error => {
          this.data = [];
          throw error;
        })
        .finally(() => {
          this.isFetching = false;
        });
    }, 500)
  }
};
</script>
<style >
.autocomplete{
  display:flex;
  align-items: center;
  justify-content: center;
  width:80%
}
.control{
  width:80%
}

</style>