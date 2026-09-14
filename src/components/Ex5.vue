<script setup>
import axios from 'axios';
import { ref } from 'vue';
const moods = ref(['Happy', 'Sad', 'Angry']);
const subject = ref('');
const entry = ref('');
const mood = ref('Happy');
const posts = ref([])

// Add Code Here

async function addPosts(subject,entry,mood) {
  const url = 'http://localhost:8000/posts'
  try {
    const response = await axios.post(url, {
        subject: subject,
        entry: entry,
        mood:  mood
    })
    // this gets the data, which is an array, and pass the data to Vue instance's posts property
    console.log(response.data)
    posts.value = response.data
  } catch (error) {
    posts.value = [{ entry: 'There was an error: ' + error.message }]
  }
}

</script>

<template>
    <div class="table m-2">
        <h3>Add a New Blog Post</h3>

        Subject: <input type='text' size='30' v-model='subject' required>
        <br>

        Entry: <br>
        <textarea name='entry' cols='80' rows='5' v-model='entry' required></textarea>
        <br>

        Mood:
        <!-- TODO: Build a dropdown list here for selecting the mood -->
        <select v-model="mood">
            <option v-for="mood in moods" :value="mood">{{mood}}</option>
        </select>
        <br>

        <br>
        <button @click="addPosts(subject,entry,mood)">Submit New Post</button>

        <hr>
        <RouterLink to="/ViewPosts/">Click  here to return to Main Page</RouterLink>  
       
    </div>
</template>

