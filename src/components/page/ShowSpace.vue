<template>
    <div>
        <ApplicationInfo :infoList="appList"></ApplicationInfo>  
    </div>
</template>
<script>
import ApplicationInfo from '@/components/common/ApplicationInfo'; 
export default {
    name:'ShowSpace',
    components:{
        ApplicationInfo
    },
    data () {
        return {
            appList:[
                  {name:'伴学网',size:'22M',value:4,text:'伴学网app是一款移动教学软件。软件已云课堂为中心，教师可直接在线为学生上课，可也自己录制视频供学生观看，在线进行信息发布等，让学生与老师关联更紧密。有需要的用户欢迎下载使用。'},
                  {name:'伴学网',size:'22M',value:4,text:'伴学网app是一款移动教学软件。软件已云课堂为中心，教师可直接在线为学生上课，可也自己录制视频供学生观看，在线进行信息发布等，让学生与老师关联更紧密。有需要的用户欢迎下载使用。'},
                  {name:'伴学网',size:'22M',value:4,text:'伴学网app是一款移动教学软件。软件已云课堂为中心，教师可直接在线为学生上课，可也自己录制视频供学生观看，在线进行信息发布等，让学生与老师关联更紧密。有需要的用户欢迎下载使用。'},
                  {name:'伴学网',size:'22M',value:4,text:'伴学网app是一款移动教学软件。软件已云课堂为中心，教师可直接在线为学生上课，可也自己录制视频供学生观看，在线进行信息发布等，让学生与老师关联更紧密。有需要的用户欢迎下载使用。'},
                  {name:'伴学网',size:'22M',value:4,text:'伴学网app是一款移动教学软件。软件已云课堂为中心，教师可直接在线为学生上课，可也自己录制视频供学生观看，在线进行信息发布等，让学生与老师关联更紧密。有需要的用户欢迎下载使用。'},
                  {name:'伴学网',size:'22M',value:4,text:'伴学网app是一款移动教学软件。软件已云课堂为中心，教师可直接在线为学生上课，可也自己录制视频供学生观看，在线进行信息发布等，让学生与老师关联更紧密。有需要的用户欢迎下载使用。'}
            ]
        }
    }
}
</script>
<style scoped>

</style>


