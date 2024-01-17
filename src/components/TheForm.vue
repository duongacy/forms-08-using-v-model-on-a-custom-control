<template>
    <div>
        <h1>The form</h1>
    </div>
    <div style="display: flex;">
        <form @submit.prevent>
            <div>
                <h3>Name</h3>
                <input type="text" v-model.trim="nameState" :class="{ error: isNameInvalid }" @blur="validateName"
                    @keypress="isNameInvalid = false">
            </div>
            <div>
                <h3>Age</h3>
                <input type="number" v-model.number="ageState">
            </div>
            <div>
                <h3>What you hear about us?</h3>
                <select v-model="referer">
                    <option value="mouth">Mouth</option>
                    <option value="google">Google</option>
                    <option value="facebook">Facebook</option>
                </select>
            </div>
            <div>
                <h3>What are you interest in?</h3>
                <label><input type="checkbox" value="css" v-model="interest">Css</label>
                <label><input type="checkbox" value="html" v-model="interest">HTML</label>
                <label><input type="checkbox" value="javascript" v-model="interest"> Javascript</label>

            </div>
            <div>
                <h3>Gender</h3>
                <label><input type="radio" v-model="gender" value="male">Male</label>
                <label><input type="radio" v-model="gender" value="female">Female</label>
                <label><input type="radio" v-model="gender" value="others">Others</label>
            </div>
            <div>
                <h3></h3>
                <label><input type="checkbox"> Did you agree with terms?</label>
            </div>
            <div>
                <h3>Rate</h3>
                <rating-control v-model="rate"></rating-control>
            </div>
            <div>
                <h3></h3>
                <button type="submit">Submit</button>
            </div>

        </form>
        <div>
            <div>Name: {{ nameState }}</div>
            <div>Age: {{ ageState }}</div>
            <div>Referer: {{ referer }}</div>
            <div>Interest: {{ JSON.stringify(interest) }}</div>
            <div>Gender: {{ gender }}</div>
            <div>Rate: {{ rate }}</div>
            <div>Agree: {{ agree }}</div>
        </div>
    </div>
</template>

<script>
import RatingControl from './RatingControl.vue'
export default {
    components: { RatingControl },
    data() {
        return {
            nameState: '',
            ageState: 0,
            referer: null,
            interest: [],
            gender: null,
            agree: false,
            rate: null,

            isNameInvalid: false
        }
    },
    methods: {
        validateName() {
            this.isNameInvalid = this.nameState === ''
        }
    }
}
</script>

<style  scoped>
.error {
    border: red solid 1px;
}
</style>