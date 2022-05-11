<template>
  <section class="news-section">
    <div class="auto-container">
      <div>
      </div>
      
      
      <div class="row clearfix">

        <div class="card">
          <ul class="list-group" style="display:flex">
            <li class="list-group-item" v-for="character in characterList" :key="character.id">
              <img v-bind:src="character.image" style="width:100%">
              <h4> {{character.id}}-{{character.name}} </h4>
              <h5>Status : {{character.status}}</h5>
              <h5>Species : {{character.species}}</h5>
              <h5>Gender : {{character.gender}}</h5>
            </li>
          </ul>
        </div>

      </div>



    </div>
  </section>
</template>

<script>
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
        created: function(){
        this.getCharacters()
    }
  }

</script>

<style scoped>



</style>
