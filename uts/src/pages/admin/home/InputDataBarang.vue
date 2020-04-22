<template xmlns:v-slot="http://www.w3.org/1999/XSL/Transform">
    <q-page padding class="items-center-justify-center bg-grey-3">
        <q-card flat class="bg-garey q-pa-md">
      <span class="text-h5 text-weight-light q-pa-md">
        <span class="text-blue-grey-14">Tambah Data Barang</span>
      </span>

            <div class="q-pa-md">
                <q-form
                        class="q-gutter-md"
                >
                    <q-input
                            label="Kode Barang"
                            lazy-rules
                            color="teal"
                            v-model="kodebarang"
                            :rules="[
                            val => val !== null && val !== '' || 'Kode Barang Dibutuhkan'
                            ]">
                        <template v-slot:append>
                            <q-icon name="dns"/>
                        </template>
                    </q-input>

                    <q-input
                            label="Brand Barang"
                            lazy-rules
                            color="teal"
                            v-model="brand"
                            :rules="[
                            val => val !== null && val !== '' || 'Brand Dibutuhkan'
                            ]">
                        <template v-slot:append>
                            <q-icon name="label"/>
                        </template>
                    </q-input>

                    <q-input
                            label="Type Baraang"
                            lazy-rules
                            color="teal"
                            v-model="type"
                            :rules="[
                            val => val !== null && val !== '' || 'Type Dibutuhkan'
                            ]">
                        <template v-slot:append>
                            <q-icon name="polymer"/>
                        </template>
                    </q-input>

                    <q-input
                            label="Garansi"
                            lazy-rules
                            color="teal"
                            v-model="garansi"
                            :rules="[
                            val => val !== null && val !== '' || 'Garansi Dibutuhkan'
                            ]">
                        <template v-slot:append>
                            <q-icon name="receipt"/>
                        </template>
                    </q-input>

                    <q-input
                            label="Berat Beban"
                            lazy-rules
                            color="teal"
                            v-model="beratbeban"
                            :rules="[
                            val => val !== null && val !== '' || 'Barat Beban Dibutuhkan'
                            ]">
                        <template v-slot:append>
                            <q-icon name="hdr_weak"/>
                        </template>
                    </q-input>

                    <q-input
                            label="Harga Barang"
                            lazy-rules
                            color="teal"
                            v-model="harga"
                            :rules="[
                            val => val !== null && val !== '' || 'Harga Dibutuhkan'
                            ]">
                        <template v-slot:append>
                            <q-icon name="local_atm"/>
                        </template>
                    </q-input>
                    <q-input
                            label="Stok Barang"
                            lazy-rules
                            color="teal"
                            v-model="stok"
                            :rules="[
                            val => val !== null && val !== '' || 'Stok Dibutuhkan'
                            ]">
                        <template v-slot:append>
                            <q-icon name="beenhere"/>
                        </template>
                    </q-input>
                    <div>
                        <q-btn
                                unelevated
                                icon="add"
                                label="Tambah Data Barang"
                                style="height: 50px"
                                color="teal-6"/>
                    </div>
                </q-form>
            </div>
        </q-card>
    </q-page>
</template>

<script>
    export default {
        data () {
            return {
                brand: null,
                kodebarang: null,
                garansi: null,
                type: null,
                beratbeban: null,
                harga: null,
                stok: null
            }
            }
        }
</script>

<style scoped>

</style>