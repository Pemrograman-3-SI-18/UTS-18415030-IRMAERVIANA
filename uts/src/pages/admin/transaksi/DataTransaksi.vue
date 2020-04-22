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

                <span class="text-h5 text-weight-light q-pa-md">
        <span class="text-weight-bold" >Data Transaksi</span>
      </span>

                <q-space />
                <q-input borderless dense debounce="300" color="mustard" v-model="filter">
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
                rowCount: 10,
                columns: [
                    {
                        name: 'desc',
                        required: true,
                        label: 'Kode Transaksi',
                        align: 'left',
                        field: row => row.kodetrx,
                        format: val => `${val}`,
                        sortable: true
                    },
                    { name: 'brand', align: 'center', label: 'Brand Mesin Cuci', field: 'brand', sortable: true },
                    { name: 'type', align: 'center', label: 'Type', field: 'type', sortable: true },
                    { name: 'garansi', label: 'Garansi', align: 'center', field: 'garansi' },
                    { name: 'beratbeban', label: 'Berat Beban', align: 'center', field: 'beratbeban' },
                    { name: 'jumbeli', label: 'Jumlah Beli', align: 'center', field: 'jumbeli' },
                    { name: 'harga', label: 'Harga', align: 'center', field: 'harga' },
                    { name: 'total', label: 'Total', align: 'center', field: 'total' }
                ],
                data: [
                    {
                        kodetrx: 'Trans01',
                        brand: 'Sharp',
                        type: 'ES-T77F',
                        garansi: '2th',
                        beratbeban: '7kg',
                        harga: '1940000',
                        jumbeli: '2',
                        total:'3880000'
                    },
                    {
                        kodetrx: 'Trans02',
                        brand: 'Sanken',
                        type: 'TW-9880',
                        garansi: '1th',
                        beratbeban: '5kg',
                        harga: '1500000',
                        jumbeli: '1',
                        total:'1500000'
                    },
                    {
                        kodetrx: 'Trans03',
                        brand: 'Toshiba',
                        type: 'VH-H75MN',
                        garansi: '1th',
                        beratbeban: '3kg',
                        harga: '1100000',
                        jumbeli: '3',
                        total:'3300000'
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