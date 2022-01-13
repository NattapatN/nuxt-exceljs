<template>
    <div class="container">
        <div>Export Excell</div>
        <button @click="onExport">download</button>
    </div>
</template>

<script>
import XLSX from 'xlsx' // import xlsx
export default {
    data() {
        return {
            exportData:[
                { name: 'Dady', age: '21' },
                { name: 'Jonh', age: '25' },
                { name: 'James', age: '17' },
            ]
        }
    },
    methods:{
        onExport(){
            const dataWS = XLSX.utils.json_to_sheet(this.exportData)
            const wb = XLSX.utils.book_new()
            XLSX.utils.book_append_sheet(wb, dataWS)
            XLSX.writeFile(wb,'export.xlsx')
        }
    }
}
</script>