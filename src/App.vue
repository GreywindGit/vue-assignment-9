<template>
    <div class="container">
        <form>
            <div class="row" v-if="!isSubmitted">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <h1>Sign Up</h1>
                    <hr>
                    <app-full-name v-model="user.fullname"></app-full-name>
                    <div class="form-group">
                        <label for="email">Email</label>
                        <input
                                type="email"
                                id="email"
                                class="form-control"
                                v-model.trim="user.email">
                    </div>
                    <div class="form-group">
                        <label for="password">Password</label>
                        <input
                                type="password"
                                id="password"
                                class="form-control"
                                v-model="user.password">
                    </div>
                    <div class="row">
                        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                            <div class="form-contro">
                                <label for="save">
                                    <input 
                                            type="checkbox"
                                            id="save"
                                            v-model="doSave">
                                    Save to Database?</label>
                            </div>
                        </div>
                    </div>
                    <hr>
                    <div class="row">
                        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                            <button
                                class="btn btn-primary"
                                @click.prevent="submitted">Submit!
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </form>
        
        <hr>
        <div class="row" v-if="isSubmitted">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <div class="panel panel-default">
                    <div class="panel-heading">
                        <h4>Your Data</h4>
                    </div>
                    <div class="panel-body">
                        <p>Full Name: {{ user.fullname }} </p>
                        <p>Mail: {{ user.email }} </p>
                        <p>Password: {{ user.password }}</p>
                        <p>Store in Database?: {{ doSave }}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import FullName from './FullName.vue';

    export default {
        data() {
            return {
                user: {
                    fullname: 'firstname lastname',
                    email: '',
                    password: ''
                },
                doSave: false,
                isSubmitted: false
            }
        },
        methods: {
            submitted() {
                this.isSubmitted = true;
            }
        },
        components: {
            appFullName: FullName
        }
    }
</script>

<style>
</style>
