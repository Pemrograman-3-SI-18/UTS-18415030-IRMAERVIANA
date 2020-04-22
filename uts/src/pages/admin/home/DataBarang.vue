<template xmlns:v-slot="http://www.w3.org/1999/XSL/Transform">

    <div class="q-pa-md">
        <q-table
                title="Treats"
                :data="data"
                :columns="columns"
                row-key="id"
                :filter="filter"
                :loading="loading"
        >

            <template v-slot:top>
                <q-btn color="lime-7" icon="payment" icon-right="send" label="Tambah Data Barang" to="/admin/inputdatabarangg"/>

                <q-space />
                <q-input borderless dense debounce="300" color="primary" v-model="filter">
                    <template v-slot:append>
                        <q-icon name="search" />
                    </template>
                </q-input>
            </template>

        </q-table>
    </div>
</template>
<script>
    export default {
        data () {
            return {
                loading: false,
                filter: '',
                rowCount: 5,
                columns: [
                    {
                        name: 'desc',
                        required: true,
                        label: 'Kode Barang',
                        align: 'left',
                        field: row => row.kodebarang,
                        format: val => `${val}`,
                        sortable: true
                    },
                    { name: 'brand', align: 'center', label: 'Brand', field: 'brand', sortable: true },
                    { name: 'type', align: 'center', label: 'Type', field: 'type', sortable: true },
                    { name: 'garansi', label: 'Garansi', align: 'center', field: 'garansi' },
                    { name: 'beratbeban', label: 'Berat Beban', align: 'center', field: 'beratbeban' },
                    { name: 'harga', label: 'Harga', align: 'center', field: 'harga' },
                    { name: 'stok', label: 'Stok', align: 'center', field: 'stok' }
                ],
                data: [
                    {
                        kodebarang: 'K01',
                        brand: 'Sharp',
                        type: 'ES-T77F',
                        garansi: '2th',
                        beratbeban: '7kg',
                        harga: '1940000',
                        stok: '3'
                    },
                    {
                        kodebarang: 'K02',
                        brand: 'Sanken',
                        type: 'TW-9880',
                        garansi: '1th',
                        beratbeban: '5kg',
                        harga: '1500000',
                        stok: '4'
                    },
                    {
                        kodebarang: 'K03',
                        brand: 'Toshiba',
                        type: 'VH-H75MN',
                        garansi: '1th',
                        beratbeban: '3kg',
                        harga: '1100000',
                        stok: '5'
                    },
                    {
                        kodebarang: 'K04',
                        brand: 'LG',
                        type: 'P905R',
                        garansi: '2th',
                        beratbeban: '5kg',
                        harga: '2532000',
                        stok: '2'
                    },
                    {
                        kodebarang: 'K05',
                        brand: 'Polytron',
                        type: 'PWM-9567',
                        garansi: '1th',
                        beratbeban: '3kg',
                        harga: '2200000',
                        stok: '5'
                    }
                ]
            }
        },

        methods: {
            // emulate fetching data from server
            addRow () {
                this.loading = true
                setTimeout(() => {
                    const
                        index = Math.floor(Math.random() * (this.data.length + 1)),
                        row = this.original[Math.floor(Math.random() * this.original.length)]
                    if (this.data.length === 0) {
                        this.rowCount = 0
                    }
                    row.id = ++this.rowCount
                    const addRow = { ...row } // extend({}, row, { name: `${row.name} (${row.__count})` })
                    this.data = [ ...this.data.slice(0, index), addRow, ...this.data.slice(index) ]
                    this.loading = false
                }, 500)
            },

            removeRow () {
                this.loading = true
                setTimeout(() => {
                    const index = Math.floor(Math.random() * this.data.length)
                    this.data = [ ...this.data.slice(0, index), ...this.data.slice(index + 1) ]
                    this.loading = false
                }, 500)
            }
        }
    }
</script>