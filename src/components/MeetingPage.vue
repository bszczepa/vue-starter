<template>
    <div>
        <button @click="toggleNewMeetingForm">Dodaj nowe spotkanie</button>
        <new-meeting-form v-if="this.showNewMeetingForm"
                          @added="addNewMeeting($event)">
        </new-meeting-form>
        <h5 v-if="this.meetings.length === 0">Brak zaplanowanych spotkań.</h5>
        <h2 v-else> Zaplanowane zajęcia ({{this.meetings.length}})</h2>
        <meetings-list :meetings="meetings"
                       :username="this.username"
                       @signup="addParticipant($event)"
                       @signout="removeParticipant($event)"
                       @deletemeeting="deleteMeeting($event)" >
        </meetings-list>
    </div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";

    export default {
        components: {NewMeetingForm, MeetingsList},
        props: ['username'],

        data() {
            return {
                meetings: [],
                showNewMeetingForm: false
            };
        },
        methods: {
            addNewMeeting(meeting) {
                this.meetings.push(meeting);
                this.toggleNewMeetingForm();
            },

            toggleNewMeetingForm() {
                this.showNewMeetingForm = !this.showNewMeetingForm;
            },

            addParticipant(meeting) {
                meeting.participants.push(this.username);
            },

            removeParticipant (meeting) {
                meeting.participants.splice(this.meetings.indexOf(meeting), 1);
            },

            deleteMeeting (meeting) {
                this.meetings.splice(this.meetings.indexOf(meeting), 1);
            }
        }
    }
</script>