<template>
    <!-- <div v-if="isAuth" class="text-center text-xs pb-2">
        <span>You are signed In </span>
        <button 
            @click="onLogOut"
            class="mt-2 text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg sm:w-auto px-2 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
            >Logout
        </button>
    </div> -->
    <footer class="bottom-0 w-full bg-gray-800 text-white">
        <div id="footer" class="flex justify-between place-items-center">
            <p class="py-2 px-4 font-semibold text-white m-auto xs:text-xs sm:text-base"><a href="/">Built with Vue and Tailwind & Firebase</a></p>
            <!-- <ul>
                <li>
                    <a href="/" class="transition duration-500 ease-in-out hover:text-white hover:bg-black">Home</a>
                </li>
                <li>
                    <router-link class="nav-link" :to="{name: 'contact'}"> 
                       Contact
                   </router-link>
                </li>
            </ul> -->
        </div>
    </footer>
</template> 
<script>
import { mapActions, mapGetters } from 'vuex'
//import Home from './home.vue'

export default {
    // components: {
    //     Home,
    // },
    computed: {
        ...mapGetters(['isAuth']),
        ...mapActions(['signOut'])
    },
    data(){
        return{
        isScrolled: false
        }
    },
    mounted(){
        window.addEventListener('scroll', this.handleScroll)
    },
    beforeUnmount(){
        window.removeEventListener('scroll', this.handleScroll)
    },
    methods:{
        handleScroll(){ 
            this.isScrolled = window.scrollY> 0;
        },
        onLogOut(){
            this.$store.dispatch('signOut')
            //this.signInAndSignUpComplete = false;
        }
    }
}
</script>
<style scoped>

#footer {
    bottom: 0;
    background-color:black;
    padding: 20px 0;
    width: 100%;
    z-index: 9999;
    transition: transform 0.2s ease-in-out;
}
nav ul{
    list-style: none;
    margin: 0;
    padding: 0;
}

nav li{
    display: inline-block;
}

nav li a {
  display: block;
  padding: 10px 20px;
  text-decoration: none;
  color: white;
  cursor: pointer;
}

</style>