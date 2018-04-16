<template>
        <uploader :options="options"  @file-success="fileSuccess">
            <uploader-btn>
                <Icon type="ios-cloud-upload-outline" size=20></Icon>
            </uploader-btn>
        </uploader>  
</template>
<script>
export default {
    name:'Upload',
    data(){
        return {
            options: {
                target: 'http://192.168.8.251/banxue/web/chunkUpload/a/uploadChunkFile',
                testChunks: false,
                forceChunkSize:true,
                token:'354374bbf8b6e0ef44b26e13eb1900cb674df11abdc98cf4f79a64a78952d3886943ba77c3f87fb94d45cf2aa30b11610662c6fa2a974a261019f03c72a9cb066fd16b92ae1c1cf28228c026138f73b739e5a7e794ac4b05ad52b7f62056135b1a127020233d4a4ec8c717953888324ad31911382e8f3060810ec7d6a50b775a0c499c805df9d0bb77651f5931a3a1433d6184f3555cc9d908bb4fb24aba4adc08311f5505777ccab3fbefbed52b46b4fa749c72b6f1cd2426bb759ed73b94f8d863cbf69239fa5864a65263c548507827629f1852ae0aea0b038f0691ff346098dd4d940ef1c265',
                simultaneousUploads:1
            },
            attrs: {
                accept: 'image/*'
            },
            statusText: {  
                success: '成功了',  
                error: '出错了',  
                uploading: '上传中',  
                paused: '暂停中',  
                waiting: '等待中'  
            }  
        }
    },
    methods:{
        // 上传成功的事件  
        fileSuccess (rootFile, file, message, chunk) {  
            console.log('complete', rootFile, file, message, chunk)  
        }	
    }
}
</script>

