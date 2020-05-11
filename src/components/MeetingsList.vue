<template>
    <table v-if="meetings.length > 0">
        <thead>
        <tr>
            <th style="width: 15%;">Nazwa spotkania</th>
            <th style="width: 15%;">Opis </th>
            <th style="width: 15%;">Uczestnicy </th>
            <th style="width: 55%; "></th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="meeting in meetings" :key="meeting.name">
            <td>{{ meeting.name }}</td>
            <td>{{ meeting.description }}</td>
            <td>
                <ul>
                    <li v-for="participant in meeting.participants" :key="participant">
                        {{participant}}
                    </li>
                </ul>
            </td>
            <td style="text-align: right">
                <button v-if="meeting.participants.indexOf(username) < 0"
                        class="button-outline"
                        @click="signUp(meeting)">
                        Zapisz się
                </button>
                <button v-else
                        class="button-outline"
                        @click="signOut(meeting)">
                        Wypisz się
                </button>
                <button v-if="meeting.participants.length === 0"
                        class=""
                        @click="deleteMeeting(meeting)">
                        Usuń puste spotkanie
                </button>
            </td>
        </tr>
        </tbody>
    </table>
</template>

<script>
    export default {
        props: ['meetings', 'username'],

        methods: {
            signUp(meeting) {
                this.$emit('signup', meeting);
            },

            signOut(meeting) {
                this.$emit('signout', meeting);
            },

            deleteMeeting(meeting) {
                this.$emit('deletemeeting', meeting);
            }

        }
    }
</script>

