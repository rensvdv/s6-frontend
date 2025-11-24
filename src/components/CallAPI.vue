<script>
import axios from "axios";

export default {
  name: "CallAPI",
  data() {
    return {
      albumData: {
        title: "",
        artist: "",
        genre: "",
        releaseDate: ""
      },
      postSuccess: false,
      postError: false
    };
  },
  methods: {
    createPost() {
      this.postSuccess = false;
      this.postError = false;

      axios.post("http://localhost:8080/api/music", this.albumData)
        .then(() => {
          this.clearForm();
          this.postSuccess = true;
        })
        .catch(() => {
          this.postError = true;
        });
    },

    clearForm() {
      this.albumData = {
        title: "",
        artist: "",
        genre: "",
        releaseDate: ""
      };
    }
  }
};
</script>

<template>
  <div class="container mt-4">
    <h3 class="mb-3">Nieuw nummer toevoegen</h3>

    <form @submit.prevent="createPost" class="card p-4 shadow-sm">
      <div class="mb-3">
        <label for="title" class="form-label">Titel</label>
        <input type="text" id="title" v-model="albumData.title" class="form-control" />
      </div>

      <div class="mb-3">
        <label for="artist" class="form-label">Artiest</label>
        <input type="text" id="artist" v-model="albumData.artist" class="form-control" />
      </div>

      <div class="mb-3">
        <label for="genre" class="form-label">Genre</label>
        <input type="text" id="genre" v-model="albumData.genre" class="form-control" />
      </div>

      <div class="mb-3">
        <label for="releasedate" class="form-label">Release date</label>
        <input type="text" id="releasedate" v-model="albumData.releaseDate" class="form-control" />
      </div>

      <button class="btn btn-primary w-100">Aanmaken</button>

      <div class="mt-3">
        <div v-if="postSuccess" class="alert alert-success">Nummer succesvol toegevoegd.</div>
        <div v-if="postError" class="alert alert-danger">Fout bij opslaan.</div>
      </div>
    </form>
  </div>
</template>
