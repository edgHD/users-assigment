<template>
    <!-- Main container for the app -->
    <div class="app-container">
        <!-- Title for the app -->
        <h1>Users on this App</h1>

        <!-- User input form component with an event to add active users -->
        <user-data @add-active-user="postActiveUser"></user-data>

        <!-- Container for displaying the list of active users -->
        <div class="active-users">
            <!-- Loop through the users array and render an ActiveUser component for each user -->
            <active-user v-for="user in users" :key="user.id" :id="user.id" :username="user.username" :age="user.age">
            </active-user>
        </div>
    </div>

    <!-- A disclaimer note :P -->
    <div class="disclaimer">
        <span>Disclaimer: Style and comments generated with Microsoft Copilot.</span>
    </div>

</template>

<script>
/* Import a UUID generation utility for creating unique IDs for users */
import uuid from './utils/uuid.js';

export default {
    data() {
        return {
            /* Array to hold all user objects, initialized with one default user */
            users: [{
                id: uuid(), // Generate a unique ID for the default user
                username: 'edgHD', // Default username
                age: this.myAge() // Call the method to calculate the default user's age
            }]
        }
    },
    methods: {
        /* Method to add a new active user to the users array */
        postActiveUser(usernameOutput, ageOutput) {
            const newUser = {
                id: uuid(), // Generate a unique ID for the new user
                username: usernameOutput, // Username input from the form
                age: ageOutput // Age input from the form
            };
            this.users.push(newUser); // Add the new user to the users array
        },
        /* Method to calculate the current age based on a birth year */
        myAge() {
            const currentMonth = new Date().getMonth(); // Get the current month (0-based index)
            const currentDay = new Date().getDate(); // Get the current day of the month
            const currentYear = new Date().getFullYear(); // Get the current year
            const birthYear = 2005; // Hardcoded birth year

            const BirthAge = currentYear - birthYear; // Calculate age by subtracting the birth year

            // Adjust the age if the current date is before the user's birthday
            if (currentMonth < 4 || (currentMonth === 4 && currentDay < 19)) {
                return BirthAge - 1;
            } else {
                return BirthAge;
            }
        }
    }
}
</script>

<style scoped>
/* Styles for the main container of the app */
.app-container {
    font-family: 'Arial', sans-serif;
    text-align: center;
    padding: 20px;
    background-color: #f9f9f9;
}

/* Styling for the main title */
h1 {
    color: #333;
    font-size: 2.2rem;
    margin-bottom: 20px;
}

/* Styling for the active users grid */
.active-users {
    display: grid;
    /* Use grid layout for user cards */
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    /* Responsive grid */
    gap: 15px;
    /* Space between user cards */
    margin-top: 20px;
}

/* Diaclaimer Style */
.disclaimer {
    font-size: 10px;
    text-align: right;
    color: #999
}
</style>
