<template>
  <div class="search">
    <div class="input-contain">
      <i class="material-icons">search</i>
      <input type="text" placeholder="Search for CSS property..." v-model="searchText" class="search-input">      
    </div>
    <div class="card" v-for="item in results">
      <div class="title">{{item.property.title}}</div>
      <div class="summary" v-html="item.property.summary"></div>
      <button class="icon-button">
        <a :href="item.property.url" target="_blank"> <i class="icon material-icons">http</i></a>
      </button>
    </div>

  </div>
</template>

<script>
export default {
  name: 'search',

  data: function() {
    return {
      mdnDocs: [],      
      searchText: '',
    }
  },
  computed: {
    results: function(){         
     return this.findMatches(this.searchText);     
    },
  },
  mounted: function() {
    this.getMdnDocs();
    
  },
  methods: {
    getMdnDocs: function() {
      this.mdnDocs = require('mdn-docs');
    },

    findMatches: function(match) {
      if(match.length > 1){
        return this.mdnDocs.filter(docs => {
          const regex = new RegExp(match, 'gi');
          return docs.property.title.match(regex);
        });
      } else{
        return this.mdnDocs;
      }
    },
 
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.card
{
    position: relative;
    z-index: 1;

    display: -ms-flexbox;
    display: flex;
    overflow: auto;
        flex-direction: column;

    border-radius: 2px;
    box-shadow: 0 1px 5px rgba(0,0,0,0.2), 0 2px 2px rgba(0,0,0,0.14), 0 3px 1px -2px rgba(0,0,0,0.12);

    -ms-flex-direction: column;
}
.title
{
    font-size: 24px;
    font-weight: 400;
    line-height: 32px;

    margin: 0;
    margin-top: 8px;

    letter-spacing: 0;
}
.summary
{
    font-size: 14px;
    font-weight: 400;
    line-height: 20px;

    margin: 0;

    letter-spacing: 0.01em;

    opacity: 0.54;
}
.input-contain
{
    position: relative;

    width: 100%;
    min-height: 48px;
    margin: 4px 0 24px;
    padding-top: 16px;

    text-align: left;
}
.input-contain:after
{
    position: absolute;
    right: 0;
    bottom: 0;
    left: 0;

    height: 1px;

    content: ' ';
    transition: all 0.4s cubic-bezier(0.25,0.8,0.25,1);

    background-color: rgba(0,0,0,0.12);
}
.icon
{
    color: rgba(0, 0, 0, 0.54);
}
.icon-button
{
    font-family: inherit;
    font-size: 14px;
    font-weight: 500;
    font-style: inherit;
    font-variant: inherit;
    
    line-height: 36px;

    position: relative;

    display: inline-block;
    overflow: hidden;

    width: 40px;
    
    min-width: 88px;
    height: 40px;
    min-height: 36px;
    
    margin: 6px 8px;
    padding: 8px;
    padding: 0 16px;

    cursor: pointer;
    -webkit-user-select: none;
       -moz-user-select: none;
        -ms-user-select: none;
            user-select: none;
    transition: all 0.4s cubic-bezier(0.25,0.8,0.25,1);
    text-align: center;
    vertical-align: top;
    white-space: nowrap;
    text-decoration: none;
    letter-spacing: inherit;
    text-transform: uppercase;

  
    color: rgba(0, 0, 0, 0.87);
    border: 0;
    border-radius: 50%;
    
    outline: none;
    background: none;
}
.search-input
{
    font-family: inherit;
    font-size: 16px;
    line-height: 32px;

    display: block;

    width: 100%;
    height: 32px;
    padding: 0;

    transition: all 0.4s cubic-bezier(0.25,0.8,0.25,1);
    transition-property: font-size;

    color: rgba(0,0,0,0.54);
    border: none;
    outline: none;
    background: none;
}

</style>
