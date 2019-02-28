<template>
    <div class="search">
        <div v-if="searchResults.length > 0">
            <div class="searchResults">
                search results:
            </div>
            <Post v-if="post < searchResults.length" v-for="(n,post) in postCount" :postData=postData[searchResults[post]]></Post>
            <div v-if="postCount < searchResults.length" class="loadMore" id="load" @mouseover="loadMoreHover" @mouseleave="loadMoreOff" v-on:click="loadMore(postData.id)">
                load more content
            </div>
         </div>
      
        <div v-else>
            <div class="searchResults">
                NO RESULTS FOUND
                <p class="centerP">consider these popular topics:</p>
                <Feature :features=featured @search-results="featureClick"></Feature>
            </div>
        </div>
        <Search v-show="false" ref="search"></Search>
    </div>
</template>
<script>
    import Post from '@/components/post.vue'
    import Feature from '@/components/feature.vue'
    import Search from '@/components/search.vue'
    export default {
        name: 'searchResults',
        components: {
            Post,
            Feature,
            Search
        },
        props: ['searchResults'],
        data() {
            return {
                featured: [{
                    name: "art",
                    imgUrl: "img.jpg"
                }, {
                    name: "design",
                    imgUrl: "img.jpg"
                }, {
                    name: "recipes",
                    imgUrl: "img.jpg"
                }],
                postCount: 5,
                postData: [{
                        title: "how to meal plan",
                        imageUrl: "img.jpg",
                        shortText: "A huge game changer for dinner time!",
                        post: ["Meal planning is something that takes a bit of time up front but leads to less time spent each night at 5:00 trying to come up with something to eat using the ingredients you already have.",
                            "Here are five things I have found useful in meal planning:",
                            "Meal planning gets easier each week as you build your recipe collection. Now that we meal plan, our food has more flavor, I have become more adventurous and confident in the kitchen, and we eat healthier. ",

                        ],
                        date: "Jan 22, 2019",
                        id: "Meal",
                        tag: "recipes cooking planning",
                        list: {
                            index: 1,
                            listItems: ["Set a date and time (or situation) in which you will meal plan. I like to do my meal planning each Saturday morning before I go to the grocery store. This way I can base our meals off what we are already buying and add whatever else we need for a recipe to our grocery list.",
                                "Figure out where you are pulling recipes from. I usually use recipes I have made in the past, have seen on Instagram, or have pinned on Pinterest. Sometimes I use cookbooks, but that usually is only if I am looking for a specific recipe. Tip: With Pinterest, I have a 'to make' section and a 'make again' section on my food board, so if I see something I would make on a regular day, I know exactly where it is. As I make each recipe, I move it to the 'make again' section so I will have a place to store all the recipes I liked, and so my 'to make' section is never very full. Check out my Pinterest using the link on the left.",
                                "Find recipes that have similar ingredients. Something that is so important to me is not wasting food. With fresh foods like produce it is easy to not eat all of them before they go bad, especially with two people. At my house, if we don’t plan specific ways to eat our vegetables, they stay forgotten in the bottom drawer of our fridge. I have found that if we find one recipe that uses a fruit or vegetable that we don’t usually just snack on, it is best to find another recipe with that ingredient and plan it for the same week. That way you are wasting less, but also saving money by buying exactly what you will use.",
                                "Write it down somewhere. I like to write our plans on a calendar we hang on our fridge. Sometimes the days get rearranged based on our schedules but everyone knowing what the plan is for the week helps so much! I generally end up scribbling ideas for the next week in the margins, which makes meal planning easier for the next week."
                            ]
                        }
                    },
                    {
                        title: "6",
                        imageUrl: 'img.jpg',
                        shortText: "Morbi feugiat nec nisl in semper. Morbi purus nibh, lobortis id congue sed, sagittis in enim. In mauris nunc, consectetur in ex sed, tincidunt facilisis nunc. Cras hendrerit tortor ac purus euismod tempor.",
                        post: [
                            "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
                            "Vivamus auctor turpis ac odio interdum posuere. Morbi rutrum risus sed neque euismod condimentum. Duis pellentesque, ",
                            "libero ut posuere pharetra, augue nulla molestie mi, convallis fringilla ante orci vel magna. Sed sit amet eros consectetur, commodo augue volutpat,",
                            " condimentum nulla. Aenean imperdiet nunc nec tincidunt gravida. Suspendisse non interdum dui. Maecenas ac elit faucibus, pretium lorem nec, tristique est. ",
                            "Duis ut neque pulvinar, efficitur nunc at, pharetra turpis.\nAenean feugiat, tortor quis efficitur tempor, lacus libero mollis tortor, sed tempor sem quam eget purus. Morbi egestas fringilla euismod. Quisque lacinia pellentesque felis, a sodales nisi condimentum vitae. Donec scelerisque interdum sapien vitae accumsan. Quisque nec est eget lectus ultricies congue. Vestibulum fringilla rhoncus tortor, sit amet cursus ante aliquam ut. Quisque accumsan fringilla erat. Maecenas faucibus iaculis sapien ut dignissim. Phasellus sit amet nulla massa.\nAenean facilisis, odio sed semper tristique, leo purus fringilla mauris, tincidunt scelerisque lectus ex id orci. Nullam at massa a sapien euismod mattis molestie cursus metus. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Aliquam sed mattis orci. Nullam vitae orci nec orci dapibus consequat. Phasellus a tortor nec nisi interdum tempus. Nulla egestas fringilla lorem, nec venenatis erat sodales tristique. Curabitur nec pharetra ex. Cras sem risus, elementum rutrum est at, tincidunt pharetra purus. Nulla molestie hendrerit dapibus. Fusce vitae scelerisque metus. Morbi aliquet et diam at luctus. Donec nec eros nec arcu maximus dignissim in sed dui. Ut quis felis ut quam consectetur aliquam id vel nulla. In sodales venenatis porta. Duis vel porttitor tellus.\n\nAliquam erat volutpat. Morbi semper metus in quam tempor pharetra. Vestibulum quis faucibus nisl. In hac habitasse platea dictumst. Proin ullamcorper nulla vel hendrerit scelerisque. Sed viverra lectus sit amet nisl eleifend porttitor. Mauris sed eros justo. Nulla at lacus in leo feugiat congue in et nunc. Quisque blandit lacus vitae magna porta pellentesque in ut magna. Suspendisse potenti. Etiam tellus risus, vulputate vitae sollicitudin nec, facilisis sit amet velit. Sed non laoreet risus, sit amet blandit nisi",
                        ],
                        date: "1.2.2019",
                        id: "mno",
                        tag: "six sixth other tag",
                        list: {
                            index: -1,
                            listItems: []
                        }
                    },
                    {
                        title: "design critique- sun tunnels",
                        imageUrl: 'sunTunnels.jpg',
                        shortText: "A brief look at the impact of Nancy Holt's environmental work located in Utah's West Desert.",
                        post: [
                            "Upon first arrival to Nancy Holt’s Sun Tunnels, the most overwhelming aspect of it all is the openness and emptiness of the environment. The 18-foot-long tunnels seem unnatural and, though aligned with one another, appear to have no connection to the world around them. All but two days of the year that is the case. On each summer and winter solstice, the cement tubes perfectly align with the rising and setting of the sun, creating a magical experience for the visitor. After such an experience, it is clear that this work was made to highlight its environment, but after further observation it is evident that this work’s purpose is much more than that. ",
                            "Being in the middle of the vast dessert, the Sun Tunnels take advantage of several environmental factors that could not be achieved elsewhere. Because of the constant movement of the sun, the light which enters from holes designed to pattern constellations varies hour to hour and day to day. The lunar cycles paired with the lack of light pollution allow the work to be viewed naturally and completely each full moon, while the entire cosmos can be observed each new moon.",
                            "The numerous references to astronomy and the movement of the earth bring the sky down to earth in the form of a tangible object which can be traversed and observed on a much smaller scale. Exploring the piece yields a deeper understanding of both the sky and the earth and how only with one can someone truly appreciate the other. The perspective provided leads to a newfound relationship between us, the earth, and the sky. ",
                            "The scale and location of the piece allows one to view it from countless perspectives including: looking in, out, through, around, into, and out of. The ability to view the piece from distinct perspectives in addition to the continuous changing of the work in relation to the sun leads us to begin to understand the complexity of the artwork in relation to its environment and in turn the complexity of any one relationship. The interactions between art and nature, sky and earth, human and environment in this piece lead to the conclusion that no relationship goes one way. ",
                            "This work succeeds at helping us understand that though we can influence our environment, both physical and situational, we will also be influenced by what surrounds us at the same time. This work would not mean the same thing if it were not for the secluded environment in which it resides. Seeing things in new perspectives we can learn about what is around us as well as learn things about ourselves in ways we couldn’t see or understand before. We can see that we are not just contributors, like the Sun Tunnels highlight their environment, but also recipients, as the environment accentuates the attributes of the Sun Tunnels."
                        ],
                        date: "Jan 15, 2019",
                        id: "scs",
                        tag: "design critique environmental fine art",
                        list: {
                            index: -1,
                            listItems: []
                        }
                    }
                ],
            }
        },
        methods: {
            featureClick: function(e) {
                this.$refs.search.searchData(e);
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
        }
    }
</script>

<style>
</style>
