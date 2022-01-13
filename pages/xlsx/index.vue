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
                { name: 'Dady', age: '21' ,test: "home" },
                { name: 'Jonh', age: '25' },
                { name: 'James', age: '17' },
            ],
        }
    },
    methods:{
        onExport(){
            // let dataWS = XLSX.utils.aoa_to_sheet(this.ws_data)
            // const dataWS = XLSX.utils.json_to_sheet(this.exportData)
            const dataWS = {
                A1: {
                    "v":"Time Period : 31/02/2021 15:00 - 01/04/2021 15:00",
                    "t":"s",
                    "s": {
                        font: {
                            sz: "24",
                        },
                    }},
                U1: {"v":"Correct answer","t":"s"},V1: {"v":"10","t":"n"},"!ref":"A1:V1" }
            console.log(JSON.stringify(dataWS))
            const wb = XLSX.utils.book_new()
            XLSX.utils.book_append_sheet(wb, dataWS)
            XLSX.writeFile(wb,'export.ods')
        }
    }
}
</script>