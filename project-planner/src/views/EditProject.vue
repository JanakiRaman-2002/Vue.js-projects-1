<template>
  <form @submit.prevent="handleEditSubmit">
    <label>Title:</label>
    <input type="text" v-model="title" required>
    <label>Details:</label>
    <textarea v-model="details" required></textarea>
    <button>Update</button>
  </form>
</template>

<script>
export default {
    props: ['id'],
    data() {
        return {
            title: '',
            details: '',
            uri: 'http://localhost:3000/projects/'+this.id,
        }
    },
    mounted() {
        fetch(this.uri)
        .then(response => response.json())
        .then(data => {
            this.title = data.title;
            this.details = data.details;
        })  
    },
    methods: {
        handleEditSubmit() {
            let project = {
                title: this.title,
                details: this.details,
            }
            fetch(this.uri, {
                method: 'PATCH',
                headers: {'Content-Type': 'application/json'},
                body: JSON.stringify(project),
            }).then(() => {
                this.$router.push('/')
            })
        }
    }
}
</script>

<style>

</style>