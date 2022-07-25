<template>
<div>
<div class="w-75 mx-auto count-wrapper">
<p>Count: <strong>{{ count }}</strong></p>
<button class="btn btn-success" @click="increment">Intracment</button>
<button class="btn btn-primary" @click="discrament">Disracment</button>
</div>

<div class="w-75 mx-auto form-div">
<h2>Add comments!</h2>
<form @submit.prevent>
<input @input="name = $event.target.value" v-bind:value="name" class="form-control" type="text" placeholder="Enter Your Name..." aria-label="text" />
<input @input="email = $event.target.value" v-bind:value="email" class="form-control my-3" type="email" placeholder="Enter Your Email..." aria-label="email" />
<input @input="content = $event.target.value" v-bind:value="content" class="form-control" type="text" placeholder="Enter Your Contents..." aria-label="text" />
<button @click="createComments" type="semailt" class="btn btn-primary mt-3">Add comments</button>
</form>
</div>

<div class="w-75 mx-auto comment" v-for="comment in comments" v-bind="comment.id">
<h2>{{ comment.name }}</h2>
<p>{{ comment.email }}</p>
<p>{{ comment.content }}</p>
</div>
</div>
</template>

<script>
export default {
data() {
    return {
    count: 0,
    comments: [
        {id: 1, name: "Otabek", email: "otabekqoldoshev96@gmail.com", content: "lorem Ipsum text"},
        {id: 2, name: "Abdulhamid", email: "abdulhamid007@gmail.com", content: "lorem Ipsum text"},
        {id: 3, name: "Ibrohim", email: "aibrohim018@gmail.com", content: "lorem Ipsum text"}
    ],
    name: "",
    email: "",
    content: "",
    }
},
methods: {
increment() {
this.count += 1
},
discrament() {
this.count -= 1
},
createComments() {
const newComment = {
id: Date.now(),
name: this.name,
email: this.email,
content: this.content
}
this.comments.push(newComment)
this.name = ""
this.email = ""
this.content = ""
}
}
}
</script>

<style>
.comment {
border: 3px solid #ccc;
padding: 10px 20px;
margin-bottom: 15px;
}

.form-div {
margin-bottom: 50px;
}
</style>