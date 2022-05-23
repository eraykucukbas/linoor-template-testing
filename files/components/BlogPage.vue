<template id="blog">
  <div class="container">
    <div class="row">
      <div>
        <div id="myModal" class="modal" :data="modalData">
          <div class="modal-content">
            <div class="text-center">
              <img class="image" :src="modalData.image">
              <h5 id="modal-title" class="title">{{modalData.id}}-{{modalData.name}}</h5>
            </div>
            <div id="modal-body" class="col text-center">
              <p><strong>Status: </strong>{{modalData.status}}</p>
              <p><strong>Status: </strong>{{modalData.species}}</p>
              <p><strong>Type: </strong>{{modalData.type}}</p>
              <p><strong>Gender: </strong>{{modalData.gender}}</p>
              <p><strong>Location: </strong>{{modalData.location.name}}</p>
              <p><strong>Origin: </strong>{{modalData.origin.name}}</p>
              <p><strong>Number of Episodes: </strong>{{modalData.episode.length}}</p>
              <p><strong>All Episodes: </strong>{{modalData.episode}}</p>
            </div>
            <button type="button" @click="closeModal" class="close">Close</button>
          </div>
        </div>
      </div>
      <div class="col-12 col-md-6 col-lg-4 p-4" v-for="character in characterList" :key="character.id">
        <div class="card" style="background: bisque">
          <img class="card-img-top" :src="character.image">
          <h5 class="card-title text-center p-2">{{character.id}}-{{character.name}}</h5>
          <div class="footer text-center">
            <button type="button" @click="showModal(character)" id="myBtn" class="btn btn-outline-success btn-block">More
              Info</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  import notFoundVue from '../pages/not-found.vue';
  import test from '../plugins/helper'
  export default {
    name: "BlogPage",
    data() {
      return {
        characterList: {},
        modalData: {
          origin: {},
          location: {},
          episode: {}
        }
      }
    },
    methods: {
      getCharacters() {
        this.$http.get("https://rickandmortyapi.com/api/character")
          .then((response) => {
            this.characterList = response.data.results;
          })
      },
      showModal: function (data) {
        let modal = document.getElementById("myModal");
        modal.style.display = "block";
        this.modalData = data;
        console.log(data.episode.length);
      },
      closeModal: function () {
        let modal = document.getElementById("myModal");
        modal.style.display = "none";
      }
    },
    created: function () {
      this.getCharacters()
    }
  }

</script>
<style scoped>
  .modal {
    display: none;
    position: fixed;
    z-index: 1;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    overflow: auto;
    background-color: rgb(0, 0, 0);
    background-color: rgba(0, 0, 0, 0.4);
  }

  .modal-content {
    background-color: bisque;
    margin: 15% auto;
    padding: 20px;
    border: 1px solid #888;
    width: 80%;
  }

  .close {
    color: #aaa;
    float: right;
    font-size: 28px;
    font-weight: bold;
  }

  .close:hover,
  .close:focus {
    color: black;
    text-decoration: none;
    cursor: pointer;
  }

  #modal-body p {
    color: rgb(0, 0, 0);
  }

</style>
