<template>
  <div id="app">
    <div class="container">
      <div class="text-center">
        <h1>Portafolo</h1>
      </div>
      <p class="text-center"><strong class="text-center">Aníbal Jorquera</strong></p>
      <div class="row margin-top">
        <div class="col-md-10 col-md-offset-1 flex">
          <card v-for="card in cards" :card="card" :random-class="classes[selectClass()]"></card>
        </div>
      </div>
      <detail ref="detail"></detail>
      <footer>
        <p class="text-center">Portafolio realizado con <3 y VueJS</p>
      </footer
    </div>
  </div>
</template>

<script>
import projects from './Components/projects.js';
export default {
  name: 'app',
  components: {
      'card': require('./Components/Card.vue'),
      'detail': require('./Components/Detail.vue')
  },
  data () {
    return {
      cards: projects,
      classes: [
        'r1',
        'r2',
        'r3'
      ]
    }
  },
  methods: {
    selectClass: function() {
      return Math.floor((Math.random() * 3));
    }
  }
}
</script>

<style lang="css">
  h1 {
    text-transform: uppercase;
    text-align: center;
    position: relative;
    color: #333;
    display: inline-block;
  }
  h1::after, h1::before {
    content: '';
    position: absolute;
    top: 50%;
    margin-top: -1px;
    height: 2px;
    background-color: #333;
    width: 90px;
  }
  h1::before {
    left: calc(-100% + 90px);
  }
  h1::after {
    right: calc(-100% + 90px);
  }
  .margin-top {
    margin-top: 45px;
  }
  footer {
    border-top: 2px solid #333;
    margin-top: 25px;
    padding: 25px;
  }
  .flex {
    display: flex;
    flex-wrap: wrap;
  }
</style>
