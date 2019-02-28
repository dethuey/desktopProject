<template>
    <div class="post">
        <img class="img" alt="Vue logo" :src="require(`@/assets/${postData.imageUrl}`)">
        
        <div class="title">
            <h2>{{postData.title}}</h2>
            <h5 class="date">{{postData.date}}</h5>
        </div>
        
        <p class="shortText" :id="'text' + postData.id ">{{postData.shortText}}</p>
        <div v-show="show && id == postData.id" class="postInfo">
            <p  v-for="(n,p) in postData.post.length">
                {{postData.post[p]}}
                <ol v-if="postData.list.index == p">
                    <li v-for="(n, s) in postData.list.listItems.length">{{postData.list.listItems[s]}}</li>
                </ol>
            </p>
            
            <div v-for="(n,q) in postData.links.length">
                <p>
                    <a class="links" :href="postData.links[q].url" target="_blank"> {{postData.links[q].link}}</a>
                    {{postData.links[q].text}}
                </p>
            </div>
            
            <a href="mailto:?Subject=Simple Share Buttons&amp;Body=I%20saw%20this%20and%20thought%20of%20you!%20 http://18.222.167.94:8080/index.html">
                <img src="https://simplesharebuttons.com/images/somacro/email.png" alt="Email" class="share" />
            </a>
            <a href="http://www.facebook.com/sharer.php?u=http://18.222.167.94:8080/index.html" target="_blank">
                <img src="https://simplesharebuttons.com/images/somacro/facebook.png" alt="Facebook" class="share"/>
            </a>
            <a href="javascript:;" onclick="window.print()">
                <img src="https://simplesharebuttons.com/images/somacro/print.png" alt="Print" class="share"/>
            </a>
            <a href="javascript:void((function()%7Bvar%20e=document.createElement('script');e.setAttribute('type','text/javascript');e.setAttribute('charset','UTF-8');e.setAttribute('src','http://assets.pinterest.com/js/pinmarklet.js?r='+Math.random()*99999999);document.body.appendChild(e)%7D)());">
                <img src="https://simplesharebuttons.com/images/somacro/pinterest.png" alt="Pinterest" class="share"/>
            </a>
        </div>
        
        
        <div :id=postData.id class="readMore" v-on:click="readMore(postData.id)" @mouseover="readMoreHover(postData.id)" @mouseleave="readMoreOff(postData.id)">read more</div>
    </div>
</template>

<script>
    export default {
        name: 'Post',
        props: ['postData'],
        data: function() {
            return {
                id: "",
                show: false
            }
        },
        methods: {
            readMore: function(postID) {
                this.id = postID;
                var id = 'text' + postID;
                if (document.getElementById(postID).innerHTML == "read more") {
                    document.getElementById(id).style.marginBottom = "30px";
                    document.getElementById(postID).innerHTML = "close";
                    this.show = true;
                }
                else {
                    document.getElementById(postID).innerHTML = "read more"
                    this.show = false;
                }
            },
            readMoreHover: function(postID) {
                document.getElementById(postID).style.backgroundColor = "#9CA673";
                document.getElementById(postID).style.color = "#4A512F";
                document.getElementById(postID).style.cursor = "pointer";

            },
            readMoreOff: function(postID) {
                document.getElementById(postID).style.backgroundColor = "#879355";
                document.getElementById(postID).style.color = "white";
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .links {
        color: #879355;
        border-bottom: 1px solid #879355;
    }

    .postInfo {
        margin-bottom: 40px;
    }

    .share {
        width: 20px;
        margin: 5px 5px 5px 0px;
    }

    li {
        margin-top: 5px;
        line-height: 1.6;
    }

    .post {
        background-color: white;
        padding: 20px;
        width: 65%;
        margin: 20px 0px;
        line-height: 1.6;
    }

    h2 {
        font-family: 'Alegreya Sans SC', sans-serif;
        font-size: 40px;
        margin: 0px 0px 0px 0px;
        font-weight: normal;
        line-height: 40px;
        color: black;
        top: 0px;
        width: 80%;
    }

    .shortText {
        font-style: italic;
    }

    .date {
        color: black;
        font-size: 14px;
        background: #fff;
        padding: 0 10px;
        right: 0;
        top: 10px;
        position: absolute;
        margin: 0;
        line-height: 14px;
        display: inline;
        font-family: 'Alegreya Sans SC', sans-serif;
    }

    .title {
        width: 100%;
        position: relative;
        margin: 0px;
    }

    .readMore {
        background-color: #879355;
        color: white;
        height: 50px;
        width: 100%;
        text-align: center;
        line-height: 50px;
        font-family: 'Alegreya Sans SC', sans-serif;
        font-size: 20px;
        font-weight: bold;
    }

    .img {
        width: 100%;
    }

    p {
        margin-top: 5px;
        font-family: 'Lora', serif;
        font-size: 15px;
    }
</style>
