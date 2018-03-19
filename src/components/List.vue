<template>
  <section>
    <header class="pokeMain__header">

    </header>
    <main class="pokeMain">
      <!--<button v-on:click="list">Load Pokemon</button>-->
      <ul class="pokeMain__list">
        <li class="pokeMain__list__item"
            v-for="item in pokemonData">
          <div class="pokeCard"
               :style="borderColor(item.type[0])">
            <img class="pokeCard__img" :src="imgPath(item.id)"/>
            <div class="pokeCard__header">
              <span class="pokeCard__header__no">#00{{ item.id }}</span>
              <h2 class="pokeCard__header__name">{{ item.name }}</h2>
              <div class="pokeCard__header__type" v-html="typeIcon(item.type[0])"></div>
              <span v-for="type in item.type">{{ type }}</span>
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
          'fire': '&#x1f525;',
          'water': '&#x1f4a7;',
          'grass': '&#x1f343;'
        };
        return '<span title="' + type + '">' + typesIcons[type] + '</span>'
      },
      borderColor: function(type) {
        let typesColors = {
          'fire': 'border-color: #E8833B',
          'water': 'border-color:#7687EE',
          'grass': 'border-color:#77CB53'
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

  .pokeCard {
    border: 1px solid;
    border-radius: 10%;
    height: 300px;
    text-align: center;
    position: relative;
  }

  .pokeCard__img {
    max-width: 200px;
    width: 100%;
    box-sizing: border-box;
    padding: 1rem;
  }

  .pokeCard__header{
    padding: .5rem;
  }

  .pokeCard__header__no,
  .pokeCard__header__name {
    display: inline-block;
  }
  .pokeCard__header__type {
    display: block;
  }
</style>
