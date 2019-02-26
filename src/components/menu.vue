<template>
    <div class="menu">
        <h1 class="title">Whirl Whim</h1>
        <div class="pages" v-for="item in menu_items" >
            <div id="item.name" v-on:click="test()">{{item.name}} </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Menu',
        methods: {
            test: function() {
                var test = this.postData;
                if (test.title == null) {
                    document.getElementById("r").style.color = "blue";
                }

            }
        },
        data: function() {
            return {
                menu_items: [{ name: "home", page: "index" }, { name: "about", page: "about" }, { name: "contact", page: "contact" }, { name: "projects", page: "projects" }]
            }
        },
        props: ["current_page"]
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .menu {
        background-color: white;
        width: 85%;
        margin-left: 10%;
        height: 100%;
        top: 0px;
        padding: 20px;
    }

    .title {
        font-family: 'Alegreya Sans SC', sans-serif;
        font-size: 7.3vw;
        margin: 20px 0px 0px 5px;
        font-weight: normal;
        line-height: 7.3vw;
    }

    .pages {
        margin: 7px 0px 0px 5px;
        font-size: 30px;
        font-family: 'Alegreya Sans SC', sans-serif;

    }

    a {
        color: black;
        text-decoration: none;
    }
</style>
