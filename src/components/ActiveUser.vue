<template>
    <!-- Container for displaying user information -->
    <div class="user-info">
        <!-- Display the username with a bold label -->
        <h2><strong>Username: </strong>{{ username }}</h2>
        <!-- Display the age with a bold label -->
        <h3><strong>Age: </strong>{{ age }}</h3>
        <!-- Display the ID with a bold label -->
        <p><strong>ID: </strong>{{ id }}</p>
    </div>
</template>

<script>
export default {
    props: {
        /* Prop to pass the user's unique ID, required and must be a string */
        id: {
            type: String,
            required: true
        },
        /* Prop to pass the user's username, required and must be a string */
        username: {
            type: String,
            required: true
        },
        /* Prop to pass the user's age, required and must be a number */
        age: {
            type: Number,
            required: true
        }
    }
}
</script>

<style scoped>
/* Styles for the user information container */
.user-info {
    border: 1px solid #ddd;
    /* Light border around the container */
    border-radius: 8px;
    /* Rounded corners */
    padding: 15px;
    /* Padding inside the container */
    background-color: #fff;
    /* White background */
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    /* Subtle shadow for a raised effect */
    text-align: left;
    /* Align text to the left */
    transition: transform 0.2s;
    /* Smooth transition for hover effect */
}

/* Add a slight zoom effect when hovering over the container */
.user-info:hover {
    transform: scale(1.05);
}

/* General margin for headings and paragraph */
h2,
h3,
p {
    margin: 8px 0;
    /* Add spacing between elements */
}

/* Styling for the strong tag in the username heading */
h2 strong {
    color: #007BFF;
    /* Blue color for emphasis */
}

/* Styling for the strong tag in age and ID elements */
h3 strong,
p strong {
    color: #6c757d;
    /* Grey color for less emphasis */
}
</style>
