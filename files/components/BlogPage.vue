<template id="blog">
  <div id="card">
    <ul class="list-group">
      <li class="list-group-item" v-for="character in characterList" :key="character.id">
        <img class="image" v-bind:src="character.image">
        <h1 id="title">{{character.id}}-{{character.name}} </h1>
        <p>Status : {{character.status}}</p>
        <p>Species : {{character.species}}</p>
        <p>Gender : {{character.gender}}</p>
      </li>
    </ul>
  </div>
</template>

<script>
  import test from '../plugins/helper'
  export default {
    name: "BlogPage",
    data() {
      return {
        characterImage: null,
        characterId: null,
        characterName: null,
        characterStatus: null,
        characterSpecies: null,
        characterGender: null,
        characterList: {}
      }
    },
    methods: {
      getCharacters() {
        this.$http.get("https://rickandmortyapi.com/api/character")
          .then((response) => {
            this.characterList = response.data.results;
          })
      }
    },
    created: function () {
      this.getCharacters()
    }
  }
</script>

<style scoped>
  #card {
    margin:5% 10%;
  }
  #card ul {
    list-style-type: none;
    display: flex;
    justify-content: space-evenly;
    flex-direction: row;
    align-items: center;
    flex-wrap: wrap;
  }
  #card ul li {
    width: 20%;
    max-width: 300px;
    margin-top: 1%;
    margin-bottom: 1%;
    padding: 0;
    border: 1px solid black;
    background-color: bisque;
  }
  #card ul li:hover {
    background-color: rgb(12, 11, 11);
  }
  #card ul li h1 {
    margin-top:2%;
    font-size: 2rem;
    text-align: center;
    color: rgb(155, 70, 235);
  }
  #card ul li p {
    font-size: 2rem;
    text-align: center;
    color: rgb(30, 204, 102);
  }
</style>
