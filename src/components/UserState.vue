<template>
    <div class="row">
        <div class="column">
            <h2>Witaj {{username}}!</h2>
        </div>
        <div class="column column-25 float-right">
            <button class="button-outline" @click="logOut()">Wyloguj</button>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['username'],

        methods: {
            logOut() {
                this.$emit('logout', this.username);
            }
        }
    }
</script>

<style scoped>

</style>