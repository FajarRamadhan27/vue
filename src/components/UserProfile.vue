<template>
  <div class="user-profile">
    <div class="user-profile_user-panel">
        <h1 class="user-profile_username"> {{ user.username }} </h1>
        
        <div class="user-profile_admin-badge" v-if="user.isAdmin">
            Admin
        </div>

        <div class="user-profile_follower-count">
            <strong>followers: </strong> {{ followers }}
        </div>
    </div>

    <div class="user-profile_tweet-wrapper">
       <TweetItem 
            v-for="tweet in user.tweets" 
            :key="tweet.id" 
            :username="user.username" 
            :tweet="tweet" 
            @favorite="toggleFavorite"
        />
    </div>
  </div>
</template>

<script>
import TweetItem from './TweetItem.vue';
    export default {
        name: 'UserProfile',
        components: { TweetItem }, 
        data() {
            return {
                followers: 0,
                user: {
                    id: 1,
                    username: '@Fr_Azhar27',
                    firtname: 'Fajar',
                    lastname: 'Ramadhan',
                    email: 'fajarramadhan220@gmail.com',
                    isAdmin: true,
                    tweets: [
                        {
                            id: 1,
                            content: "twotter is amazing"
                        },
                        {
                            id: 2,
                            content: "Dont forge to subscriber to the earth is square",
                        },
                        {
                            id: 3,
                            content: "Dont forge to subscriber to the earth is square",
                        },
                        {
                            id: 4,
                            content: "Dont forge to subscriber to the earth is square",
                        }
                    ]
                }
            }
        },

        watch: {
            follower(newFollowerCount, oldFollowerCount) {
                if (oldFollowerCount < newFollowerCount) {
                    console.log(`${this.user.username} has gained a follower!`);
                }
            }
        },

        computed: {
            fullName() {
                return `${this.user.firtname} ${this.user.lastname}`
            }
        },

        methods: {
            followUser() {
                this.followers++;
            },
            toggleFavorite(id) {
                console.log(`favorite tweet #${id}`)
            }
        },

        // running when component loaded
        mounted() {
            this.followUser()
        }
    }
</script>

<style>
.user-profile {
    display: grid;
    grid-template-columns: 1fr 3fr;
    grid-gap: 50px;
    padding: 50px 5%;
}

.user-profile_user-panel {
    display: flex;
    flex-direction: column;
    padding: 20px;
    background-color: white;
    border-radius: 5px;
    border: 1px solid #DFE3E8;
}

.user-profile_admin-badge {
  background:rebeccapurple;
  color: white;
  border-radius: 5px;
  margin-right: auto;
  padding: 0 10px;
  font-weight: bold;
}

h1 {
    margin: 0;
}

.user-profile_tweet-wrapper {
    display: grid;
    grid-gap: 10px;
}
</style>