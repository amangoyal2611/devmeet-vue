<template>
    <v-container>
        <v-layout row wrap>
            <v-flex xs12 sm6 class="text-sm-right text-xs-center">
                <v-btn large router to="/meetups">Explore Meetup</v-btn>
            </v-flex>
            <v-flex xs12 sm6 class="text-sm-left text-xs-center">
                <v-btn large color="primary" router to="/meetup/new">Organize a meetup</v-btn>
            </v-flex>
        </v-layout>
        <v-layout>
            <v-flex xs12 class="ma-2">
                <v-carousel>
                    <v-carousel-item
                            v-for="item in meetups"
                            :key="item.id"
                            :src="item.imageUrl"
                            @click="toLoadMeetup(item.id)"
                    >
                        <div class="title">{{item.title}}</div>
                    </v-carousel-item>
                </v-carousel>
            </v-flex>
        </v-layout>
        <v-layout row wrap class="mt-2">
            <v-flex xs12 class="text-xs-center">
                <p>Join our awesome meetups!</p>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
    export default {
        computed: {
            meetups() {
                return this.$store.getters.featuredMeetups
            }
        },
        methods: {
            toLoadMeetup(id) {
                this.$router.push('/meetup/' + id)
            }
        }
    }
</script>

<style scoped>
    .title {
        position: absolute;
        bottom: 50px;
        margin: auto;
        background-color: rgba(0, 0, 0, 0.5);
        color: #fff;
        font-size: 2em;
        padding: 30px;
    }
</style>