<template>
    <div id="app">

        <ul v-if="posts && posts.length">
            <li v-for="post of posts">
                <p><strong>{{post.Name}}</strong></p>
                <p><strong>{{post.Email}}</strong></p>

            </li>
        </ul>

        <ul v-if="errors && errors.length">
            <li v-for="error of errors">
                {{error.message}}
            </li>
        </ul>
    </div>

</template>

<script>
    import axios from 'axios';

    export default {
        data() {
            return {
                posts: [],
                errors: []
            }
        },

        // Fetches posts when the component is created.
        created() {
            axios.get(`http://localhost:10000/users`)
                .then(response => {
                // JSON responses are automatically parsed.
                this.posts = response.data
                    console.log(this.posts);
        })
        .
            catch(e => {
                this.errors.push(e)
        })

        }
    }
</script>