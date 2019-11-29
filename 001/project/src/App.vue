<template>
  <div id="app">
    <div>{{ message }}</div>
    <div v-if="seen">fuga</div>
    <a v-bind:href="url">bbbbbbbbbb</a>
    <div :id="a">v-bind:id</div>
    <div>
      <a v-on:click="clickHandler">jijojiojijoj</a>
    </div>
    <div>
      {{ computedMessage  }}
    </div>
    <div>
      {{ b }}
    </div>
    <a v-on:click="bUpdateHandler">
      b updater
    </a>
    <div>
      {{ c }}
    </div>
    <a v-on:click="cUpdateHandler">
      c updater
    </a>
    <ul>
      <li v-for="(item, index) in items" :key="item +index">
        {{ item }}
      </li>
    </ul>
    <HelloWorld />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'app',
  data() {
    return {
      message: 'hoge',
      seen: false,
      url: 'http://hoge',
      a: 'piyo',
      b: 'b-hoge',
      c: 'c-fuga',
      items: [
        0, 1, 2,
      ]
    }
  },
  components: {
    HelloWorld,
  },
  computed: {
    computedMessage() {
      return this.message + 'fuga'
    },
    seenData: {
      get() {
        return this.seen
      },
      set(b) {
        this.seen = b
      },
    },
    bData: {
      get() {
        return this.b
      },
      set(v) {
        this.b = this.b + v
      }
    }
  },
  methods: {
    clickHandler() {
      alert('bbbbbbb')
    },
    bUpdateHandler() {
      this.bData = 'aaaaaaaa'
    },
    cUpdateHandler() {
      this.c = this.c + 'aaaaaaaa'
    }
  },
  mounted() {
    this.seenData = true
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
