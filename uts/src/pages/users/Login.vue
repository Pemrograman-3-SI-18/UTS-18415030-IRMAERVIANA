<template>
    <q-layout class="bg-blue-grey-1" view="hHr LpR lFf">
        <q-page-container>
            <q-page padding class="row items-center justify-center">
                <div class="row full-width">
                    <div class="col-md-8 offsett-md-2 col-xs-15 q-pl-md q-pr-md q-pt-sm">
                        <q-card flat class="bg-white text-black">
                            <div class="row">
                                <div class="col-md-6 col-xs-15">
                                    <div class="row q-pt-md q-pb-md bg-white">
                                        <div class="col-md-9 offset-1 col-xs-9">
                                            <q-img spinner-color="white" placeholfer-src="statics/group.png" src=
                                                    "statics/icons/group.png"></q-img>
                                        </div>
                                    </div>
                                </div>
                                <div class="col-md-6 col-xs-12 q-pt-md">
                                    <div class="q-pa-md">


                                        <q-card-section class="text-blue-14">
                                            <div class="text-brown-14 text-h4">Login</div>
                                        </q-card-section>

                                        <q-form
                                                @submit="onSubmit"
                                                @reset="onReset"
                                                class="q-gutter-md">

                                            <q-input
                                                    filled
                                                    v-model="username"
                                                    label="Username"
                                                    hint="Username"
                                                    lazy-rules
                                                    :rules="[ val => val && val.length > 0 || 'Data tidak boleh kosong']"
                                            />

                                            <q-input
                                                    filled
                                                    type="password"
                                                    v-model="pw"
                                                    label="password"
                                                    hint="password"
                                                    lazy-rules
                                                    :rules="[ val => val && val.length > 0 || 'Data tidak boleh kosong']"
                                            />


                                            <div>
                                                <q-btn label="Login" type="submit" to="/pembeli" color="primary"/>
                                                <q-btn label="Registrasi" to="/auth/registrasi" color="primary" flat class="q-ml-sm" />
                                            </div>
                                        </q-form>

                                    </div>
                                </div>
                            </div>

                        </q-card>

                    </div>

                </div>

            </q-page>
        </q-page-container>
    </q-layout>
</template>

<script>
    export default {
        name: 'Login',
        data () {
            return {
                username: null,
                pw: null,

                accept: false
            }
        },

        methods: {
            onSubmit () {
                if (this.accept !== true) {
                    this.$q.notify({
                        color: 'red-5',
                        textColor: 'white',
                        icon: 'warning',
                        message: 'You need to accept the license and terms first'
                    })
                }
                else {
                    this.$q.notify({
                        color: 'green-4',
                        textColor: 'white',
                        icon: 'cloud_done',
                        message: 'Submitted'
                    })
                }
            },

            onReset () {
                this.name = null
                this.age = null
                this.accept = false
            }
        }
    }
</script>

<style scoped>

</style>