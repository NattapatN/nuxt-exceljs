<template>
    <div class="container">
        <div>Export Excell</div>
        <button @click="onExport">download</button>
    </div>
</template>

<script>
import * as Excel from "exceljs/dist/exceljs.min.js";
import * as ExcelProper from "exceljs";
import * as FileSaver from 'file-saver';
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
        async onExport(){
            let workbook= new Excel.Workbook();
            var worksheet = workbook.addWorksheet('My Sheet');

            worksheet.columns = [
            { header: 'Id', key: 'id', width: 10 },
            { header: 'Name', key: 'name', width: 32 },
            { header: 'D.O.B.', key: 'DOB', width: 10 }
            ];
            worksheet.getCell('A1').fill = {
                type: 'pattern',
                pattern:'darkVertical',
                fgColor:{argb:'FFFF00'}
            };
            worksheet.addRow({ id: 1, name: 'Ionic Android', dob: new Date(1970, 1, 1) });
            worksheet.addRow({ id: 2, name: 'Ionic iOS', dob: new Date(1965, 1, 7) });
            var tempFilePath = 'PATH/temp.xlsx'; // PATH is where you want to create your file

            workbook.xlsx.writeBuffer().then(buffer => FileSaver.saveAs(new Blob([buffer]), `${Date.now()}_feedback.xlsx`)).catch(err => console.log('Error writing excel export', err))
        }
    }
}
</script>