<template>
  <div id="app">      
    <search></search>  
  </div>
</template>

<script>
import Search from './components/Search'

export default {
  name: 'app',
  
  components: {
    Search
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
  width: 33%;
  margin: 0 auto;
  
}

html *, html :after, html :before {
    box-sizing: inherit;
}

body{
      font-size: 14px;
    letter-spacing: .01em;
        font-weight: 400;
    line-height: 20px;
        min-height: 100%;
    margin: 0;
    position: relative;
    -webkit-tap-highlight-color: transparent;
    -webkit-touch-callout: none;
    -webkit-text-size-adjust: 100%;
    -ms-text-size-adjust: 100%;
    -moz-osx-font-smoothing: grayscale;
    -webkit-font-smoothing: antialiased;
    color: rgba(0,0,0,.87);
    font-family: Roboto,Noto Sans,Noto,sans-serif;
}
</style>
