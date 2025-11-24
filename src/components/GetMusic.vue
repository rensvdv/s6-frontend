<script>
import axios from "axios";

export default {
  name: "GetMusic",
  data() {
    return {
      musicList: [],
      loadError: false
    };
  },

  mounted() {
    this.fetchMusic();
  },

  methods: {
    fetchMusic() {
      axios.get("http://localhost:8080/api/music")
        .then(response => {
          this.musicList = response.data;
        })
        .catch(() => {
          this.loadError = true;
        });
    }
  }
};
</script>

<template>
  <div class="container mt-4">
    <h3 class="mb-3">Alle nummers</h3>

    <div v-if="loadError" class="alert alert-danger">
      Kon de nummers niet ophalen.
    </div>

    <div class="row">
      <div
        v-for="music in musicList"
        :key="music.id"
        class="col-md-6 col-lg-4 mb-4"
      >
        <div class="card shadow-sm h-100">
          <div class="card-body">
            <h5 class="card-title">{{ music.title }}</h5>
            <h6 class="card-subtitle text-muted mb-2">{{ music.artist }}</h6>

            <p class="mb-1"><strong>Genre:</strong> {{ music.genre }}</p>
            <p class="mb-1"><strong>Release:</strong> {{ music.releaseDate }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
