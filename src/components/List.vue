<template>
  <section>
    <header class="pokeMain__header">

    </header>
    <main class="pokeMain">
      <!--<button v-on:click="list">Load Pokemon</button>-->
      <ul class="pokeMain__list">
        <li class="pokeMain__list__item"
            v-for="item in pokemonData">
          <div class="pokeTile"
               :style="borderColor(item.type[0])">
            <img class="pokeTile__img" :src="imgPath(item.id)"/>
            <div class="pokeTile__header">
              <span class="pokeTile__header__no">#00{{ item.id }}</span>
              <h2 class="pokeTile__header__name">{{ item.name }}</h2>
              <div class="pokeTile__header__type" v-html="typeIcon(item.type[0])"></div>
              <span v-for="type in item.type" class="pokeTile__typeLabel">{{ type }}</span>
            </div>
          </div>
        </li>
      </ul>
    </main>
  </section>
</template>

<script>
  import pokemonData from '../../static/pokedex.json'

  export default {
    name: 'list',
    data: function() {
      return {
        pokemonData,
      }
    },
    methods: {
      imgPath: function(int) {
        return require('../assets/img/00' + int + '.png');
      },
      typeIcon: function(type) {
        let typesIcons = {
          'Fire': '&#x1f525;',
          'Water': '&#x1f4a7;',
          'Grass': '&#x1f343;'
        };
        return '<span title="' + type + '">' + typesIcons[type] + '</span>'
      },
      borderColor: function(type) {
        let typesColors = {
          'Fire': 'border-color: #E8833B',
          'Water': 'border-color:#7687EE',
          'Grass': 'border-color:#77CB53'
        };
        return typesColors[type]
      }
    }
  }
</script>

<style scoped>
  .pokeMain {
    max-width: 1100px;
    margin: 0 auto;
    padding: 1rem;
    border: 1px solid deeppink;
  }

  .pokeMain__list {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
  }

  .pokeMain__list__item {
    position: relative;
    cursor: pointer;
    box-sizing: border-box;
    display: block;
    width: 30%;
    height: auto;
    margin: 1rem;
    padding: .5rem;
    overflow: hidden;
    transition: all 0.3s;
  }

  .pokeMain__list__item:hover {
    transform: scale(1.1);
    transition: all 0.3s;
  }

  .pokeTile {
    border: 1px solid;
    border-radius: 10%;
    min-height: 300px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }

  .pokeTile::after {
    content: "";
    position: absolute;
    top: -110%;
    left: -220%;
    z-index: -1;


    width: 200%;
    height: 200%;
    opacity: 1;
    transform: rotate(30deg);

    background: rgba(255, 255, 255, 0.13);
    background: linear-gradient(
      to right,
      rgba(255, 255, 255, 0.13) 0%,
      rgba(255, 255, 255, 0.13) 77%,
      rgba(255, 255, 255, 0.5) 92%,
      rgba(255, 255, 255, 0.0) 100%
    );
  }

  .pokeTile:hover::after {
    opacity: 1;
    top: -30%;
    left: -30%;
    transition-property: left, top, opacity;
    transition-duration: 0.7s, 0.7s, 0.15s;
    transition-timing-function: ease;
  }

  .pokeTile__img {
    max-width: 200px;
    width: 100%;
    box-sizing: border-box;
    padding: 1rem;
  }

  .pokeTile__header {
    display: block;
    background: rgba(255,255,255,0.2);
    padding: .5rem;
    margin-bottom: 1rem;
  }

  .pokeTile__header__no,
  .pokeTile__header__name {
    display: inline-block;
  }
  .pokeTile__header__type {
    display: block;
  }

  .pokeTile__typeLabel {
    background: rgba(255,255,255,0.4);
    display: inline-block;
    box-sizing: border-box;
    border-radius: 10px;
    padding: .25rem .4rem;
    margin: .3rem .5rem;
    min-width: 4rem;
    font-size: .75rem;
    font-family: sans-serif;
  }

  .pokeTile__typeLabel::first-letter {

  }



  /* Glare animation */
  @keyframes slide {
    0% {transform:translateX(-100%);}
    100% {transform:translateX(100%);}
  }

</style>
