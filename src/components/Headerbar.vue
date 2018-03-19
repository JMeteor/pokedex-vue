<template>
    <header class="mainHeader">
      <img src="../assets/logo.svg" alt="logo"/>
      <nav class="navigation">
        <ul class="navigation__list">
          <li class="navigation__listItem">Home</li>
          <li class="navigation__listItem">Search</li>
          <li class="navigation__listItem">About</li>
          <li class="navigation__listItem">Support</li>
        </ul>
      </nav>
    </header>
</template>

<script>
    export default {
        name: "headerbar"
    }
</script>

<style scoped>
  .mainHeader {
    background: rgba(0,0,0,0.2);
    min-height: 10rem;
    text-align: center;
  }

  .navigation {
    padding-bottom: 1rem;
  }

  .navigation__list {
    list-style-type: none;
    display: flex;
    justify-content: center;
  }

  .navigation__listItem {
    position: relative;
    cursor: pointer;
    padding: .4rem .5rem;
    margin: 0 1rem;
    font-size: 1.25rem;
  }

  .navigation__listItem::before {
    content: "";
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 1px;
    background-color: #fff;
    visibility: hidden;
    transform: scaleX(0);
    transition: all 0.5s ease-in-out;
  }

  .navigation__listItem:hover::before {
    visibility: visible;
    transform: scaleX(1);
  }



</style>
