<template>
    <div class="search">
        <form v-on:submit.prevent="onSubmit">
            <input id="searchBar" type="text" ref="search">
            <br>
            <input class="submit" type="submit" value="Submit">
        </form> 
    </div>
</template>

<script>
    export default {
        name: 'Post',
        props: ['postData'],
        data: function() {
            return {
                searchResults: []
            }
        },
        methods: {
            onSubmit: function(e) {
                var query = this.$refs.search.value;
                this.searchData(query);
            },
            searchData: function(query) {
                query = query.toUpperCase();

                this.searchResults = [];
                var shortText = [];
                var postArray = [];
                var tag = []
                for (var i = 0; i < this.postData.length; i++) {
                    console.log(this.postData[i]);
                    //check all post titles first
                    if (this.postData[i].title.toUpperCase().includes(query)) {
                        console.log(this.postData[i].title.toUpperCase());
                        console.log(query);
                        this.searchResults.push(i);
                    } //check all short text second
                    else if (this.postData[i].shortText.toUpperCase().indexOf(query) != -1) {
                        console.log("2");
                        shortText.push(i);
                    } //check all tags next
                    else if (this.postData[i].tag.toUpperCase().indexOf(query) != -1) {
                        console.log("3");
                        tag.push(i);
                    } //lastly check post content
                    else {
                        for (var r = 0; r < this.postData[i].post.length; r++) {
                            if (this.postData[i].post[0].toUpperCase().indexOf(query) != -1) {
                                postArray.push(i);
                                break;
                            }
                        }
                    }
                }
                this.searchResults = this.searchResults.concat(shortText).concat(tag).concat(postArray);
                //check all post short text second
                document.getElementById("searchBar").value = "";
                this.$emit('search-results', this.searchResults)
            }
        }
    }
</script>
<style scoped>
    .search {
        margin-top: 159 px;
    }

    input[type=text] {
        width: 100%;
        padding: 12px 20px;
        margin: 3px 0;
        box-sizing: border-box;
        background-color: white;
        background-image: url('../assets/searchIcon.png');
        background-position: 10px 10px;
        background-repeat: no-repeat;
        padding-left: 40px;
        border: none;
        border-bottom: 1px solid #879355;
        -webkit-transition: 0.2s;
    }

    input[type=text]:focus {
        outline: none;
        -webkit-appearance: none;
        border: none;
        border-bottom: 3px solid #879355;
    }

    .submit {
        display: none;
    }
</style>
