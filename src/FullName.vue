<template>
    <div class="form-group">
        <div class="form-group">
            <label for="firstname">First Name</label>
            <input
                    type="text"
                    id="firstname"
                    class="form-control"
                    :value="firstname"
                    @change="nameChanged(true, $event)">
        </div>
        <div class="form-group">
            <label for="lastname">Last Name</label>
            <input
                    type="text"
                    id="lastname"
                    class="form-control"
                    :value="lastname"
                    @change="nameChanged(false, $event)">
        </div>
    </div>
</template>

<script>
export default {
    props: {
        value: String
    },
    methods: {
        nameChanged(isFirst, event) {
            let name = '';
            if (isFirst) {
                name = event.target.value + ' ' + this.lastname;
            } else {
                name = this.firstname + ' ' + event.target.value;
            }
            this.$emit('input', name);
        }
    },
    computed: {
        firstname() {
            return this.value.split(' ').slice(0, -1).join(' '); 
        },
        lastname() {
            return this.value.split(' ').pop();
        }
    }
}
</script>