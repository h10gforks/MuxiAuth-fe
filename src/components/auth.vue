<template>
    <div class="wrap">
        <div class="full-width main-color full-height">
            <div class="main margin full-height">
                <div class="left-right inline-block vertical-align margin">
                    <div class="circle">
                    </div>
                </div>
                <div class="right left-right inline-block vertical-align">
                    <div class="container margin">
                        <div class="text-align router-margin">
                            <router-link to="/" class="btn transparent">
                                <a v-on:click="tologin" v-bind:class="{highlight: login}">登录</a>
                            </router-link>
                            <router-link to="/register" class="registerButton btn transparent">
                                <a v-on:click="toregister" v-bind:class="{ highlight: !login}">注册</a>
                            </router-link>
                        </div>
                        <router-view></router-view>
                    </div>
                </div>
            </div>
        </div>
        <div class="footer full-width">
            <div class="center margin">
               
            </div>
        </div>
    </div>
</template>

<script>
    import Login from './login.vue'
    import Register from './register.vue'
    import Cookie from '../Cookie.js'
    
    export default {
        data() {
            return {
                login: true
            }
        },
        components: {
            "login": Login,
            "register": Register
        },
        methods: {
            tologin: function() {
                this.login = true
            },
            toregister: function() {
                this.login = false
            }
        },
        mounted() {
            if (window.location.href.includes('landing')) {
	            let index = window.location.href.indexOf('landing');
	            let lands = window.location.href.slice(index+8);
                let land = decodeURIComponent(lands);

                let lastChar = land[land.length-1];
                if (lastChar !== '/') land += '/';
                Cookie.setCookie("land", land);
            }
        }
    }
</script>

<style lang="sass">
@import '../pc.scss';
.highlight {
    color: #0b2029;
}

.btn {
    font-size: 14px;
    border: none;
    color: #878583;
}

.container {
    width: 202px;
}

.box-height {
    height: 30px;
}

.registerButton {
    margin-left: 14px;
}

.eye {
    width: 20px;
}
</style>
