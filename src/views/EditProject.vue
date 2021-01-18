<template>
    <form>
        <label>Title</label>
        <input type="text" v-model="title" required>
        <label>Details</label>
        <input type="text" v-model="details" required>
        <button>Update Project</button>
    </form>
</template>

<script>
export default {
    props: ['id'],
    data() {
        return {
            title: '',
            details: '',
            uri: 'http://localhost:3000/projects/' + this.id
        }
    },
    mounted() {
        fetch(this.uri)
        .then(res => res.json())
        .then(data => {
            this.title = data.title
            this.details = data.details
        }).catch(err => console.log(err))
    }
}
</script>
