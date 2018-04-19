<script type="text/javascript">
const per2gradeList=[
			{id:1,name:"高中",gradeList:[{id:10,name:"高一"},{id:11,name:"高二"},{id:12,name:"高三"},]},
            {id:2,name:"初中",gradeList:[{id:7,name:"初一"},{id:8,name:"初二"},{id:9,name:"初三"},]},
            {id:3,name:"小学",gradeList:[{id:1,name:"一年级"},{id:2,name:"二年级"},{id:3,name:"三年级"},{id:4,name:"四年级"},{id:5,name:"五年级"},{id:6,name:"六年级"}]},
            {id:0,name:"专题",gradeList:[{id:13,name:"小升初"},{id:14,name:"中考"},{id:15,name:"高考"}]}
            ];
const subjectList=[   
                {id:0,name:'全部'},             
                {id:1,name:'语文'},
                {id:2,name:'数学'},
                {id:3,name:'英语'},
                {id:4,name:'物理'},
                {id:5,name:'化学'},
                {id:6,name:'地理'},
                {id:7,name:'历史'},
                {id:8,name:'政治'},
                {id:9,name:'生物'},
            ];
const colorList = [
  '#58c33b',
  '#83a9ff',
  '#83a9ff',
  '#1cb0ea',
  '#bb73ff',
  '#e7c332',
  '#ff8383',
  '#ffa751',
  '#3bc385',
  '#808080',
];
function setFileType(fileType,size){
    let imgUrl=''
    switch(fileType){
        case 'doc':
        case 'docx':
            imgUrl='/static/imgs/resource/fileDoc.png';
            break;
        case 'jpg':
          imgUrl='/static/imgs/resource/fileJpg.png';
          break;
        case 'mp3':
          imgUrl='/static/imgs/resource/fileMp3.png';
          break;
        case 'pdf':
          imgUrl='/static/imgs/resource/filePdf.png';
          break;
        case 'png':
          imgUrl='/static/imgs/resource/filePng.png';
          break;
        case 'ppt':
        case 'pptx':
          imgUrl='/static/imgs/resource/filePpt.png';
          break;
        case 'rar':
          imgUrl='/static/imgs/resource/fileRar.png';
          break;
        case 'txt':
          imgUrl='/static/imgs/resource/fileTxt.png';
          break;
        case 'mp4':
        case 'flv':
        case 'wav':
        case 'avi':
        case 'mkv':
        case 'rmvb':
          imgUrl='/static/imgs/resource/fileVideo.png';
          break;
        case 'xls':
        case 'xlsx':
          imgUrl='/static/imgs/resource/fileXls.png';
          break;
        case 'zip':
          imgUrl='/static/imgs/resource/fileZip.png';
          break;
        default:
          imgUrl='/static/imgs/resource/fileunkonw.png';
    }
    if(size==1){//1:小图，其他：大图
        imgUrl=imgUrl.split('.')[0]+'1.'+imgUrl.split('.')[1]
    }
    return imgUrl;
}
const colorListLength =10;
function getRandColor () {
  var tem = Math.round(Math.random() * colorListLength)
  return colorList[tem]
}            		
export default
{
  per2gradeList,
  subjectList,
  colorList,
  colorListLength,
  getRandColor,
  setFileType
}
</script>