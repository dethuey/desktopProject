<template>
  <div class="about content">
    <img class="image" :src="require(`@/assets/${about.img[0]}`)">
    <h3>about</h3>
    <p v-for="(n,p) in about.content.length">
      {{about.content[p]}}
    </p>
  </div>
</template>

<script>
  export default {
    name: 'about',
    data() {
      return {
        about: {
          content: [
            "Whirl Whim was created to document the implementation of design in everyday experiences and its consequences. It has become a place to share the crucial role art and design have on user experiences.",
            "Whirl Whim is run by Danielle Case, a computer scientist and creative who values the joy brought by good design, simplicity, art, planning, and intentional living. Here she will share the effects art and design have on society, and how culture, art, and intentionalism shape our perspectives, opinions, and experiences."
          ],
          img: [
            "img.jpg",
            "sunTunnels.jpg",
            "vue.jpg"
          ]
        },
      }
    },
    methods: {
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
    }
  }
</script>
<style>
</style>
