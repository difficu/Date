<template>
  <input type="text" ref="text" v-model="num" @blur="formD(num , 'yyyy-MM-dd HH:mm:ss 星期w')">
  <p>{{num}}</p>
  <p>{{format}}</p>
</template>

<script>
// import func from 'vue-editor-bridge'
  export default{
   name:'Date',
   data(){
     return {
       num:'',
       date:'',
       format:'yyyy-MM-dd HH:mm:ss 星期w'
     }
   },
   created(){
     console.log(new Date(1409894060000).getDate())
   },
   methods:{
     formD(val , f){
       var d = new Date(val)
       var reg = {
        yyyy:d.getFullYear(),
        yy:(""+ d.getFullYear()).slice(-2),
        M:d.getMonth()+1,
        MM:("0"+ (d.getMonth()+1)).slice(-2),
        d:d.getDate(),
        dd:("0" + d.getDate()).slice(-2),
        H:d.getHours(),
        HH:("0" + d.getHours()).slice(-2),
        h:d.getHours() % 12,
        hh:("0"+d.getHours() % 12).slice(-2),
        m:d.getMinutes(),
        mm:("0" + d.getMinutes()).slice(-2),
        s:d.getSeconds(),
        ss:("0" + d.getSeconds()).slice(-2),
        w:['日', '一', '二', '三', '四', '五', '六'][d.getDay()]

       }

       this.format = f.replace(/([a-z]+)/ig,function($1){return reg[$1]});
       console.log(this.format)
       return this.format

     }
   }
}
</script>

<style scoped>

</style>