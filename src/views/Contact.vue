<template>
    <div class="content contact">
        <p class="centerP">{{contact.text}} <a class="emailLink" :href="'mailto:' + contact.link">{{contact.link}}</a></p>
    </div>
</template>

<script>
    export default {
        name: 'contact',
        data() {
            return {
                contact: {
                    text: "For more information about the mission of Whirl Whim, collaborative inquiries, or other questions please contact us via email:",
                    link: "danielle@whirlwhim.com."
                }
            }
        }
    }
</script>

<style>
    .contact {
        margin-top: 100px;
    }
</style>
