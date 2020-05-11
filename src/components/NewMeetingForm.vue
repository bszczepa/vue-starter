<template>
    <form @submit.prevent="addNewMeeting()">
        <h3>Dodaj nowe spotkanie</h3>
        <label>Nazwa</label>
        <input type="text" v-model="newMeeting.name">
        <label>Opis</label>
        <textarea v-model="newMeeting.description"></textarea>
        <button>Dodaj</button>
        <h6 v-if="showNameAlert" style="margin-left: 10px; color: #fc0000; display: inline-block ">Spotkanie musi mieć nazwę!</h6>
    </form>
</template>

<script>
    export default {
        data() {
            return {
                newMeeting: {participants: []},
                showNameAlert: false
            };
        },
        methods: {
            addNewMeeting() {
                if (this.newMeeting.name) {
                    this.$emit('added', this.newMeeting);
                } else {
                    this.showNameAlert = true;
                }
            }
        }
    }
</script>