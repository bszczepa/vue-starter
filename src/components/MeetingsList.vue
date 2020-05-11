<template>
    <table v-if="meetings.length > 0">
        <thead>
        <tr>
            <th>Nazwa spotkania</th>
            <th>Opis</th>
            <th>Uczestnicy</th>
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
            <td>
                <button class="button-outline" @click="signUp(meeting)">Zapisz się</button>
                <button class="button-outline" @click="signOut(meeting)">Wypisz się</button>
                <button @click="deleteMeeting(meeting)">Usuń puste spotkanie</button>
            </td>
            <td></td>
        </tr>
        </tbody>
    </table>
</template>

<script>
    export default {
        props: ['meetings'],

        methods: {
            signUp(meeting) {
                this.$emit('signup', this.meeting);
            },

            signOut(meeting) {
                this.$emit('signout', this.meeting);
            },

            deleteMeeting(meeting) {
                this.$emit('deletemeeting', this.meeting);
            }

        }
    }
</script>