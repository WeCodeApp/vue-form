<template>
    <form>
        <label for="email">Email</label>
        <input type="text" required v-model="email">

        <label for="password">Password</label>
        <input type="password" required v-model="password">

        <label for="role">Role</label>
        <select v-model="role">
            <option value="developer"> Web Developer </option>
            <option value="designer"> Web Designer </option>
        </select>

        <div>
            <input type="checkbox" v-model="terms" required>
            <label for="terms">Accept terms and condition</label>
        </div>
        
        <label for="skills">Skills</label>
        <input type="text" required v-model="tempSkill" @keyup="addSkill">
        <div v-for="skill in skills" :key="skill" class="pill" @click="">
            <span>{{ skill }}</span>
        </div>
    </form>
        
    <p> Email: {{ email }}</p>
    <p> Password: {{ password }}</p>
    <p> Role: {{ role }}</p>
    <p> Terms accepted: {{ terms }}</p>
</template>

<script>
    export default {
        data() {
            return {
                email: 'mario',
                password: '',
                role: 'developer',
                terms: false,
                tempSkill: '',
                skills: []
            }
        },
        methods: {
            addSkill(e) {
                console.log(e)
                if (e.key === 'Enter') {
                    if (!this.skills.includes(this.tempSkill)){
                        this.skills.push(this.tempSkill)
                    }
                    this.tempSkill = ''
                }
            }
        }
    }
</script>

<style>
form {
max-width: 420px;
margin: 30px auto;
background: 'white';
text-align: left;
padding: 40px;
border-radius: 10px;
background: lightpink;
}

label {
color: #000;
display: inline-block;
margin: 25px 0 15px;
font-size: 0.6em;
text-transform: uppercase;
letter-spacing: 1px;
font-weight: bold;
}

input, select {
display: block;
padding: 10px 6px;
width: 100%;
box-sizing: border-box;
border: none;
border-bottom: 1px solid #ddd;
color: #555;
}

input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
}

.pill {
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
}

</style>