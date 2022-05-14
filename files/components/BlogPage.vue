<template>
  <section>
    <div>
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
    </div>


  </section>


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
  div {
    display: inline-block;
    margin: 5%;
  }

  ul {
    display: inline-block;
  }

  li {
    display: inline-block;
    list-style: none;
    margin: 2%;
    padding: 0%;
    box-sizing: border-box;
    border: 1px solid black;
    border-radius: 1%;
    background-color: bisque;
  }

  .image {
    display: inline-block;
  }



  #title {
    color: rgb(155, 70, 235);
    font-family: fantasy;

  }

  p {
    color: rgb(30, 204, 102);
    font-weight: bold;

  }

  h1,
  p {
    font-size: 100%;
    margin: 1%;
    text-align: center;
  }

</style>
