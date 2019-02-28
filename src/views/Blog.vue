<template>
    <div class="blog">
        <Post v-if="post < postData.length" v-for="(n,post) in postCount" :postData=postData[post]></Post>
        <div v-if="postCount < postData.length" class="loadMore" id="load" @mouseover="loadMoreHover" @mouseleave="loadMoreOff" v-on:click="loadMore(postData.id)">
          load more content
        </div>
    </div>
</template>

<script>
    import Post from '@/components/post.vue'
    export default {
        name: 'blog',
        components: {
            Post
        },
        data() {
            return {
                postCount: 4,
                postData: [{
                        title: "Potassium Chlorate and the IKEA Effect",
                        imageUrl: 'ikea.jpg',
                        shortText: "How the discover of early french chemist lead to the theory of the IKEA effect",
                        post: [
                            "Claude-Louis Berthollet was born in rural France in 1748. He traveled to Paris where he studied medicine. Bored by the medical practice Berthollet was constantly experimenting with chemicals and became well known for his chemical compounds. In his research for developing a substitution for saltpeter, commonly used to make gun powder, Berthollet created the compound Potassium Chlorate. Astounded by its explosive abilities, Bethollet lead a public demonstration of gun powder created with the new compound which resulted in the deaths of 5 people. Because its instability, potassium could not be used in gunpowder, but its influence lead to several other discoveries.",
                            "In the early 1800’s English chemist and druggist John Walker struck a small stick on his fireplace and it caught flame. He had discovered the first friction match. The stick had been soaked in sulfur, and tipped with potassium chlorate, chlorate of potash, and gum. Walker had found a way to contain the explosive properties of potassium chlorate in the first simple and quick way to make fire. His invention sparked several chemist and inventors to develop safer options including the safety match in Sweden.",
                            "Without the invention of matches, the life of young Ingvar Kamprad would have ended completely differently. Ingvar began a profitable business at age 5 by selling matches he had bought in bulk to his neighbors at low rates. This ignited an entrepreneurial itch that lead him to start his business at age 17. Ingvar wanted to buy matches at distributor prices and thus had to build a company. He used his initials and the name of his home town in naming his company: IKEA. His products switch from matches and other small household products to furniture and over the years the IKEA empire was founded on flat-box, build-it-yourself furnishings",
                            "IKEA quickly spread across much of the world and with it what has now been termed as the IKEA effect. Founded on research with IKEA furnishings, the IKEA effect is essentially the increased value and pride in an object that one partially creates. Because of the popularity of IKEA across the world, this effect was easily detected and researched, and its findings confirm the long time theory that work makes for a happy more satisfying life. "
                        ],
                        date: "Feb 3, 2019",
                        id: "ikea",
                        tag: "science influence design research",
                        list: {
                            index: -1,
                            listItems: []
                        },
                        links: [],
                        credit: "image from ikea.com"
                    },
                    {
                        title: "how to meal plan",
                        imageUrl: "meal-plan-template.jpg",
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
                        },
                        links: [],
                        credit: "picture from crystalkarges.com"
                    }, {
                        title: "hope you had a lovely weekend",
                        imageUrl: 'flowers2.jpg',
                        shortText: "",
                        post: [
                            "Hope you all have had a lovely weekend. I was glad to get a little more sleep and take a little care  of me and our apartment. Sundays are my favorite days. I try to not work and just focus on being present. Today we spend time with family, make a yummy meal, and had a nice relaxing day. Here are some links from around the web to help you ease into the work week!"
                        ],
                        date: "Feb 16, 2019",
                        id: "s216",
                        tag: "Friday links",
                        list: {
                            index: -1,
                            listItems: []
                        },
                        links: [{
                                url: "https://meaningfuleats.com/instant-pot-sausage-lentil-stew/",
                                link: "A delicious lentil stew",
                                text: ""
                            },
                            {
                                url: "https://cupofjo.com/2017/10/amanda-jane-jones-house-tour/",
                                link: "This house tour",
                                text: " is just perfect! I love the design and simplicity"
                            },
                            {
                                url: "https://experiments.withgoogle.com/collection/arts-culture",
                                link: "Google Arts Experiments",
                                text: " inspire me so much by showing the power of technology and art."
                            }, {
                                url: "http://www.melissakaseman.com/#/preschool-pocket-treasures/",
                                link: "Preschool pocket treasures",
                                text: ""
                            }
                        ],
                        credit: "picture from cupofjo.com"

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
                        },
                        links: [],
                        credit: ""
                    }, {
                        title: "Have a Wonderful Weekend",
                        imageUrl: 'cactus.jpg',
                        shortText: "",
                        post: [
                            "I am so excited for this weekend! It will be a busy one, but a nice change from the work and school week. My mom, aunt and I planned a luncheon baby shower for my sister with some friends and the menu could scream spring any more. I can’t wait to taste all the recipes and see how things get decorated. Here is what we will be cooking up this weekend:"
                        ],
                        date: "Jan 31, 2019",
                        id: "s131",
                        tag: "Friday links",
                        list: {
                            index: -1,
                            listItems: []
                        },
                        links: [{
                                url: "https://www.loveandzest.com/avocado-chicken-caesar-salad/",
                                link: "The yummiest looking caesar salad",
                                text: ""
                            },
                            {
                                url: "http://www.bakinbit.com/2014/02/12/grapefruit-berries-honey-and-mint-salad/",
                                link: "A monochromatic fruit salad",
                                text: " looks oh so delicious."
                            },
                            {
                                url: "https://www.thebakingchocolatess.com/best-lemon-bars/",
                                link: "Lemon bars",
                                text: " are one of my absolute favorite desserts!"
                            }, {
                                url: "https://www.greensnchocolate.com/2015/08/triple-berry-vanilla-cream-pie/",
                                link: "This cream cake",
                                text: " we are making in the form of mini triffles"
                            }
                        ],
                        credit: ""

                    }

                ],
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
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
