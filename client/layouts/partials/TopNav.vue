<template>
    <nav class="navbar is-transparent">
        <div class="navbar-brand">
            <nuxt-link class="navbar-item" :to="{name: 'index'}">
                <img src="https://bulma.io/images/bulma-logo.png" alt="Bulma: a modern CSS framework based on Flexbox" width="112" height="28">
            </nuxt-link>
            <div class="navbar-burger burger" data-target="navbarExampleTransparentExample">
                <span></span>
                <span></span>
                <span></span>
            </div>
        </div>
        <div id="navbarExampleTransparentExample" class="navbar-menu">
            <div class="navbar-end">
                <template v-if="!authenticated">
                    <div class="navbar-item">
                        <div class="field is-grouped">
                            <p class="control">
                                <nuxt-link :to="{ name: 'auth-signin'}" class="button is-text"> Sign in</nuxt-link>
                            </p>
                            <p class="control">
                                <nuxt-link :to="{ name: 'auth-signup'}" class="button is-text"> Sign up</nuxt-link>
                            </p>
                        </div>
                    </div>
                </template>
                <template v-if="authenticated">
                    <div class="navbar-item has-dropdown is-hoverable">
                        <a class="navbar-link"> {{ user.name}}</a>
                        <div class="navbar-dropdown is-boxed">
                            <a class="navbar-item" @click.prevent="logout"> Logout</a>
                        </div>
                    </div>    
                </template>
                            
            </div>
        </div>
    </nav>

</template>

<script>

import { mapGetters } from  'vuex'

export default {
   methods: {
       logout () {
           this.$auth.logout();
       }
   }
}
</script>

