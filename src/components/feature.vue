<template>
    <div class=featured>
        <div class="element" v-for="post in features" @click="test(post.name)">
            <img class="image" :src="require(`@/assets/${post.imgUrl}`)" >
            {{post.name}}
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Feature',
        props: ['features'],
        methods: {
            test: function(name) {
                this.$emit('search-results', name);
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .element {
        width: 30%;
        background-color: white;
        box-sizing: border-box;
        height: 250px;
        float: left;
        margin: 1.5%;
        padding: 10px;
        cursor: pointer;
    }

    .featured {
        width: 100%;
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
</style>
