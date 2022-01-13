<template>
    <div class="container">
        <div>Export Excell</div>
        <button @click="onExport">download</button>
    </div>
</template>

<script>
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
        }
    }
}
</script>