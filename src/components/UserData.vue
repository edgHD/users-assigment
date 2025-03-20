<template>
    <!-- Form container for adding a new user -->
    <form @submit.prevent="addActiveUser" class="user-form">
        <!-- Group for the username input -->
        <div class="form-group">
            <!-- Label for the username input -->
            <label for="username">Username</label>
            <!-- Text input for username, bound to 'usernameInput' via v-model -->
            <input id="username" type="text" placeholder="Username" v-model="usernameInput">
        </div>
        <!-- Group for the age input -->
        <div class="form-group">
            <!-- Label for the age input -->
            <label for="age">Age</label>
            <!-- Number input for age, bound to 'ageInput' via v-model -->
            <input id="age" type="number" placeholder="Age" v-model="ageInput">
        </div>
        <!-- Submit button -->
        <button type="submit" class="btn">Add User</button>
    </form>
</template>

<script>
export default {
    // Define an event this component emits
    emits: ['add-active-user'],
    data() {
        return {
            // Reactive data for form inputs
            usernameInput: '', // Holds the username from the input
            ageInput: null // Holds the age from the input
        };
    },
    methods: {
        // Method to add a new active user
        addActiveUser() {
            // Check if both inputs are valid (username is not empty and age is provided)
            if (this.usernameInput?.trim() && this.ageInput) {
                // Emit the 'add-active-user' event with the input values
                this.$emit(
                    'add-active-user',
                    this.usernameInput,
                    this.ageInput
                );
                // Reset the form inputs after submission
                this.usernameInput = '';
                this.ageInput = null;
            } else {
                // Show an alert if inputs are invalid
                alert('You should fill both username and age!');
            }
        }
    }
};
</script>

<style scoped>
/* Style for the form container */
.user-form {
    max-width: 400px;
    /* Limit the form width */
    margin: 0 auto;
    /* Center the form */
    padding: 20px;
    /* Add padding inside the form */
    border: 1px solid #ddd;
    /* Add a light border */
    border-radius: 8px;
    /* Rounded corners for the form */
    background-color: #fefefe;
    /* White background */
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    /* Subtle shadow for a raised effect */
}

/* Style for each input group in the form */
.form-group {
    margin-bottom: 15px;
    /* Space between input groups */
}

/* Style for labels */
label {
    display: block;
    /* Ensure the label is on its own line */
    margin-bottom: 5px;
    /* Space below the label */
    color: #333;
    /* Dark text color */
    font-weight: bold;
    /* Bold text */
}

/* Style for input fields */
input {
    width: 90%;
    /* Full width for input fields */
    padding: 10px;
    /* Add padding inside the input */
    border: 1px solid #ccc;
    /* Light border for inputs */
    border-radius: 5px;
    /* Rounded corners */
    font-size: 1rem;
    /* Consistent font size */
    background-color: #f9f9f9;
    /* Light gray background */
}

/* Style for input fields when focused */
input:focus {
    outline: none;
    /* Remove default outline */
    border-color: #007BFF;
    /* Blue border on focus */
    background-color: #fff;
    /* Change background to white */
}

/* Style for the submit button */
.btn {
    display: inline-block;
    /* Button as an inline block element */
    width: 100%;
    /* Full width button */
    padding: 10px 15px;
    /* Padding inside the button */
    font-size: 1.1rem;
    /* Larger font size */
    background-color: #007BFF;
    /* Blue background */
    color: #fff;
    /* White text */
    border: none;
    /* Remove border */
    border-radius: 5px;
    /* Rounded corners */
    cursor: pointer;
    /* Pointer cursor on hover */
    text-transform: uppercase;
    /* Uppercase text */
}

/* Style for the submit button on hover */
.btn:hover {
    background-color: #0056b3;
    /* Darker blue on hover */
}
</style>
