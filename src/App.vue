<template>
  <div id="app">
    <Headerbar/>
    <main>
      <Search/>
      <List/>
    </main>
    <Footerbar/>
  </div>
</template>

<script>
import Headerbar from './components/Headerbar'
import Search from './components/Search'
import List from './components/List'
import Footerbar from './components/Footerbar'

export default {
  name: 'App',
  components: {
    Headerbar,
    Search,
    List,
    Footerbar
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Cinzel+Decorative:400,700|Nunito:600');
  * {
    margin: 0;
    padding: 0;
  }

  body {
    min-height: 100vh;
    color: #fff;
    font-family: Cinzel Decorative, sans-serif;
    background: linear-gradient(#c33764, #1d2671);
  }
</style>
