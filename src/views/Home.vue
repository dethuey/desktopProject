<template>
  <div class="home">
    
  
  <div class="left">
      <div class="menu">
        <h1 class="title" id="title" v-on:click="menuChange('home')" @mouseover="mouseover('title')">Whirl Whim</h1>
        <div id="pages" class="pages" v-for="item in menu_items" >
            <div class="page" :id=item.name v-on:click="menuChange(item.page)" @mouseover="mouseover(item.name)">{{item.name}} </div>
        </div>
        <search ref="search" :postData=postData @search-results="updateSearch"></search>
        <a :href="follow.url" target="_blank" v-for="follow in follow_items" >
          <img :id="follow.alt" class="followIcon" alt="follow.alt" :src="require(`@/assets/${follow.imageUrl}`)">
        </a>
      </div>
    </div>
    
    <div class="right">
      
      <div v-if="currentPage == 'home'">
        <Post v-if="post < postData.length" v-for="(n,post) in postCount" :postData=postData[post]></Post>
        <div v-if="postCount < postData.length"class="loadMore" id="load" @mouseover="loadMoreHover" @mouseleave="loadMoreOff" v-on:click="loadMore(postData.id)">
          load more content
        </div>
      </div>
      
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
      
      <div class="content" v-if="currentPage == 'about'">
        <img class="image" :src="require(`@/assets/${about.img[0]}`)">
        <h3>about</h3>
        <p v-for="(n,p) in about.content.length">
          {{about.content[p]}}
        </p>
      </div>
      <div class="content" v-if="currentPage === 'contact'">
        <p class="centerP">{{contact.text}} <a class="emailLink" :href="'mailto:' + contact.link">{{contact.link}}</a></p>
      </div>
      
      <div class= "footer">
        design created by Danielle Case
      </div>
      
    </div>
  </div>
  </div>
</template> //
<script>
  //   // @ is an alias to /src
  //   import HelloWorld from '@/components/HelloWorld.vue'

  //   export default {
  //     name: 'home',
  //     components: {
  //       HelloWorld
  //     }
  //   }
  //
</script>

<script>
  import Post from '@/components/post.vue'
  import Search from '@/components/search.vue'
  import Feature from '@/components/feature.vue'

  export default {
    name: 'home',
    components: {
      Post,
      Search,
      Feature
    },
    props: ['postData', 'menu_items', 'about', 'follow_items', 'featured', 'contact'],
    methods: {
      updateSearch: function(e) {
        this.postCount = 5;

        if (e.length == 0) {
          this.currentPage = "emptySearch";
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
