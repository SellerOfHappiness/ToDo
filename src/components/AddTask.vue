<template>
    <div>
        <form @submit.prevent="onSubmit">
            <input type="text" v-model="title">
            <button class="btn">Добавить задачу</button>
        </form>
    </div>
</template>

<script>
export default {
    data() {
        return {
            title: ''
        }
    },
    methods: {
        onSubmit() {
            this.$emit('add-task', {
                id: Date.now(),
                title: this.title,
                done: false
            })

            this.title =''
        }
    },
}
</script>

<style scope>
form {
    display: flex;
    align-items: baseline;
}

input {
    height: 29px;
    border: 2px solid;
    margin-right: 15px;
    width: 100%;
    padding: 0 15px;
}

button {
    width: 100%;
    max-width: 150px;
}
</style>