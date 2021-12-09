<template>
  <div id="app">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/International_Pok%C3%A9mon_logo.svg/2560px-International_Pok%C3%A9mon_logo.svg.png"
    height="100px"
    width="250px" ></img>
    <br></br>
    <!-- <br> <img id="imggg" style="width: 20%" src="http://assets.stickpng.com/thumbs/58482acecef1014c0b5e4a1e.png">
    </br></br><button v-on:click="logg">Log</button>
    <button v-on:click="disp">Disparaitre</button>
    <button v-on:click="appa">Apparaitre</button>
    <button v-on:click="imgg">Image</button> -->
    <input type="text" id="input" placeholder="Numéro du Pokémon">
    <button v-on:click="ok">OK</button>
      <br></br> 
    <b id="nomPokemon"></b>
      <br></br> 
    <b id="typePokemon"></b>
      <br></br> 
    <b id="pvPokemon"></b>
      <br></br> 
    <img src="" id="imgPokemon"></img>
  </div>
  
</template>

<script>
import axios from 'axios';
export default {
  name: 'HelloWorld',
  // data () {
  //   return {
  //     msg: 'Welcome to Your Vue.js App'
  //   }
  // }, methods : {
  //   logg : function (event) {
  //     console.log("press")
  //   },

  //   disp : function(event){
  //     text.style.display = "none";
  //   },

  //   appa : function(event){
  //     text.style.display = "block";
  //   },

  //   imgg : function(event){
     
  //    if(imggg.src != "https://www.lsa-conso.fr/mediatheque/6/8/0/000362086_5.jpg" ){

  //    imggg.src = "https://www.lsa-conso.fr/mediatheque/6/8/0/000362086_5.jpg"

  //    } else {
  //      imggg.src = "http://assets.stickpng.com/thumbs/58482acecef1014c0b5e4a1e.png"
  //    }
  //   }
  data () {
    return {
      info: null
    }
  },
  methods: {

  ok : function () {
    const idd = input.value
    const url = 'https://pokeapi.co/api/v2/pokemon/' + idd
    axios
      .get(url)
      .then(function (response) {
        console.log(response);
        nomPokemon.innerHTML = " NOM : " + response.data.species.name
        typePokemon.innerHTML = response.data.types[0].type.name
           if (response.data.types.length != 1){
             typePokemon.innerHTML = " TYPE : "+ response.data.types[0].type.name + "/" + response.data.types[1].type.name
          } else {
            typePokemon.innerHTML = " TYPE : "+ response.data.types[0].type.name
          }
        imgPokemon.src = response.data.sprites.front_shiny
        pvPokemon.innerHTML = " PV : " + response.data.base_experience
      })
    }
  }

}
</script>
  <style scoped>
/* Global styles */
.btn {
  padding: 0.8rem 1rem 0.7rem;
  border: 0.2rem solid #4d4d4d;
  cursor: pointer;
  text-transform: capitalize;
}
/* End global styles */
#app {
  background: #fff;
  margin: 2rem 0 4rem 0;
  padding: 1rem;
  padding-top: 0;
  position: relative;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.2), 0 2.5rem 5rem 0 rgba(0, 0, 0, 0.1);
  background-image: url(https://wallpapers.com/images/high/all-yellow-pikachu-1tizawb0hfiga8zt.jpg)
  

}
@media screen and (min-width: 550px) {
  #app {
    padding: 4rem;
  }
}
#app > * {
  max-width: 50rem;
  margin-left: auto;
  margin-right: auto;
}
#app > form {
  max-width: 100%;
}
#app h1 {
  display: block;
  min-width: 100%;
  width: 100%;
  text-align: center;
  margin: 0;
  margin-bottom: 1rem;
}

</style>
