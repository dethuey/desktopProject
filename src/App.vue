<template>
<div id="nav">
      <router-link to="/">Home</router-link> |
      <!--<router-link to="/about":postData="postData" :menu_items, 'about', 'follow_items', 'featured', 'contact'>About</router-link>-->
      
      <div class="left">
        <div class="menu">
          <router-link to='/'><h1 class="title" id="title" v-on:click="menuChange('blog')" @mouseover="mouseover('title')">Whirl Whim</h1></router-link>
            <div id="pages" class="pages" v-for="item in menu_items">
              <router-link class="page" :to='"/" + item.page' @mouseover="mouseover(item.name)"><div class="page" v-on:click="menuChange(item.page)" :id=item.name>{{item.name}}</div></router-link>
            </div>
          <search ref="search" :postData=postData @search-results="updateSearch"></search>
          <a :href="follow.url" target="_blank" v-for="follow in follow_items" >
            <img :id="follow.alt" class="followIcon" alt="follow.alt" :src="require(`@/assets/${follow.imageUrl}`)">
          </a>
        </div>
      </div>
      <div class="right">
        <div v-if="currentPage == 'search'">
          <div class="searchResults">
            search results:
          </div>
          <Post v-if="post < searchResults.length" v-for="(n,post) in postCount" :postData=postData[searchResults[post]]></Post>
          <div v-if="postCount < searchResults.length" class="loadMore" id="load" @mouseover="loadMoreHover" @mouseleave="loadMoreOff" v-on:click="loadMore(postData.id)">
            load more content
          </div>
        </div>
      
        <div v-if="currentPage == 'emptySearch'">
          <div class="searchResults">
            NO RESULTS FOUND
            <p class="centerP">consider these popular topics:</p>
            <Feature :features=featured @search-results="featureClick"></Feature>
          </div>
        </div>
        <router-view/>
        <div class= "footer">
        design created by Danielle Case
      </div>
    </div>
      
    
  </div>
</template>

<script>
  import Post from './components/post.vue'
  import Search from './components/search.vue'
  import Feature from './components/feature.vue'

  export default {
    name: 'app',
    components: {
      Post,
      Search,
      Feature
    },
    props: ['postData', 'menu_items', 'about', 'follow_items', 'featured', 'contact'],
    methods: {
      updateSearch: function(e) {
        this.postCount = 5;
        console.log(e);
        this.$router.push({ path: 'search' });
        if (e.length == 0) {
          this.currentPage = "emptySearch";
          //add router.push here
          this.searchResults = e;
        }
        else {
          this.currentPage = "search";
          this.searchResults = e;
        }
        this.scrollToTop();
      },
      featureClick: function(e) {
        this.$refs.search.searchData(e);
      },
      mouseover: function(id) {
        document.getElementById(id).style.cursor = "pointer";
      },
      loadMoreHover: function() {
        document.getElementById("load").style.borderColor = "#879355";
        document.getElementById("load").style.backgroundColor = "#9CA673";
        document.getElementById("load").style.color = "#F0EFEF";
        document.getElementById("load").style.cursor = "pointer";
      },
      loadMoreOff: function() {
        document.getElementById("load").style.borderColor = "#879355";
        document.getElementById("load").style.backgroundColor = "#F0EFEF";
        document.getElementById("load").style.color = "#879355";
      },
      loadMore: function() {
        this.postCount += 5;
        if (this.postCount >= this.postData.length) {
          document.getElementById("load").style.visibility = "hidden";
        }
      },
      scrollToTop: function() {
        window.scrollTo(0, 0);
      },
      menuChange: function(change) {
        this.postCount = 5;
        this.currentPage = change;
        for (var i = 0; i < this.menu_items.length; i++) {
          if (this.menu_items[i].page == this.currentPage) {

            document.getElementById(this.menu_items[i].name).style.borderBottom = "thick solid #879355";
          }
          else {
            document.getElementById(this.menu_items[i].name).style.borderBottom = "thin solid #879355";
          }
        }
        this.scrollToTop();
      }
    },
    data: function() {
      return {
        postCount: 5,
        currentPage: "home",
        searchResults: []
      }
    }
  }
</script>

<style>
  #blog {
    border-bottom: 3px solid #879355;
  }

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    background-color: #F0EFEF;
  }

  .followIcon {
    width: 10%;
    margin: 3px;
    margin-top: 10px;
  }

  .loadMore {
    box-sizing: border-box;
    padding: 20px;
    width: 69%;
    margin: 20px 0px 90px 0px;
    border-style: solid;
    border-width: 3px;
    color: #879355;
    font-size: 20px;
    font-weight: bold;
    text-align: center;
    font-family: 'Alegreya Sans SC', sans-serif;

  }

  .left {
    background: #F0EFEF;
    position: fixed;
    left: 0;
    top: 0;
    bottom: 0;
    right: 75%;
    overflow: hidden;
  }

  .right {
    background: #F0EFEF;
    position: absolute;
    left: 35%;
    top: 0;
    bottom: 0;
    right: 0;
    min-height: 1000px;
  }

  body {
    background-color: #F0EFEF;
  }

  .menu {
    background-color: white;
    width: 85%;
    margin-left: 10%;
    height: 100%;
    top: 0px;
    padding: 20px;
  }

  .emailLink {
    color: #879355;
    border-bottom: thin solid #879355;

  }

  .title {
    font-family: 'Alegreya Sans SC', sans-serif;
    font-size: 7.3vw;
    margin: 20px 0px 0px 5px;
    font-weight: normal;
    line-height: 7.3vw;
  }

  .pages {
    margin: 7 px 0 px 0 px 5 px;
    font-size: 30px;
    font-family: 'Alegreya Sans SC', sans-serif;
  }

  .page {
    border-bottom: thin solid #879355;
    width: 100%;
  }

  .image {
    width: 100%;
  }

  .searchResults {
    font-size: 40px;
    font-family: 'Alegreya Sans SC', sans-serif;
    margin-top: 100px;
    text-align: center;
    width: 70%;
  }

  .content {
    width: 65%;
    margin-top: 50px;
  }

  .footer {
    width: 70%;
    height: 200px;
    padding: 80px 0px;
    text-align: center;
    font-size: 16px;
    font-family: 'Alegreya Sans SC', sans-serif;

  }

  p {
    font-size: 15px;
    font-family: 'Lora', serif;
    text-align: left;
  }

  .centerP {
    font-size: 30px;
    font-family: 'Alegreya Sans SC', sans-serif;
    margin-top: 30px;
    text-align: center;
  }

  a {
    color: black;
    text-decoration: none;
  }

  h3 {
    font-size: 40px;
    font-family: 'Alegreya Sans SC', sans-serif;
    margin-top: 10px;
    font-weight: normal;
    margin-bottom: 0px;
    line-height: 40px;
    border-bottom: thin solid #879355;
  }
</style>
