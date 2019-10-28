<template>
  <div class="refferbox">
   
    <div class="reffertable_box">
	  <table class="reffertable">
      <tr>
        <td><img class="refferpic" :src="quakelogo" @click="quakebtn"/></td>
        <td><img class="refferpic" :src="resonatelogo" @click="resonatebtn"/></td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td @click="quakebtn">{{$t("message.quake")}}</td>
        <td @click="resonatebtn">{{$t("message.resonate")}}</td>
        <td></td>
        <td></td>
        
      </tr>
    </table>
    <table class="reffertable">
      <!-- <tr>
        <td><img class="refferpic" :src="zerodicelogo" @click="zerodicelogobtn"/></td>
        <td><img class="refferpic" :src="blockoptions" @click="blockoptionsbtn"/></td>
        <td></td>
        <td></td>
        
      </tr> -->
      <!-- <tr>
        <td @click="zerodicelogobtn">{{$t("message.zerodicelogo")}}</td>
        <td @click="blockoptionsbtn">{{$t("message.blockoptions")}}</td>
        <td @click="gowinplusbtn">{{$t("message.gowinplus")}}</td>
        <td></td>
        
      </tr> -->
    </table>
    </div>
    <div v-show="isshowtoast" class="isshowclass">
      <p>{{$t("message.updating")}}</p>
      <span class="closeclass" @click="closedivbtn">{{$t("message.close")}}</span>
    </div>
  </div>
</template>

<script>
import Links from '../../common/links'
import trans from '../../common/utils/trans'
export default {
  name: 'MainScreen',
  components:{
  },
  data () {
    return {
      quakelogo:'static/images/quakelogo.png',
      resonatelogo:'static/images/resonatelogo.png',
      isshowtoast:false
    }
  },
  mounted() {

  },
  methods: {
    quakebtn:function (event) {      
      let dname = window.localStorage.getItem("Quake");
      if(dname){
        window.open(Links.url.quake,'_self')
      }else{
        trans.$emit("tipsemit",{"name":"QUAKE","link":Links.url.quake,"state":0});
      }
    },
    resonatebtn:function(event){
      let dname = window.localStorage.getItem("Resonate");
      if(dname){
        window.open(Links.url.resonate,'_self')
      }else{
        trans.$emit("tipsemit",{"name":"Resonate","link":Links.url.resonate,"state":0});
      }
    },
    blockoptionsbtn:function(){
      
      let dname = window.localStorage.getItem("Blockoptions");
      if(dname){
        window.open(Links.url.blockoptions,'_self')
      }else{
        trans.$emit("tipsemit",{"name":"Blockoptions","link":Links.url.blockoptions,"state":0});
      }
    },
    zerodicelogobtn:function(){
      let dname = window.localStorage.getItem("Zerodicelogo");
      if(dname){
        window.open(Links.url.zerodicelogo,'_self')
      }else{
        trans.$emit("tipsemit",{"name":"ZeroDice","link":Links.url.zerodicelogo,"state":0});
      }
    },
    phoenixbtn:function(){
      let dname = window.localStorage.getItem("Phoenix");
      if(dname){
        window.open(Links.url.phoenix,'_self')
      }else{
        trans.$emit("tipsemit",{"name":"Phoenix","link":Links.url.phoenix,"state":0});
      }
    },
    gowinlogobtn:function(){
      let dname = window.localStorage.getItem("gowin");
      if(dname){
        window.open(Links.url.gowin,'_self')
      }else{
        trans.$emit("tipsemit",{"name":"gowin","link":Links.url.gowin,"state":0});
      }
    },
    gowinplusbtn:function(){
      let dname = window.localStorage.getItem("TreasureBasin");
      if(dname){
        window.open(Links.url.gowin_plus,'_self')
      }else{
        trans.$emit("tipsemit",{"name":"TreasureBasin","link":Links.url.gowin_plus,"state":0});
      }
    },
    closedivbtn:function(){
      this.isshowtoast=false
    }
  }
}
</script>

<style>
.isshowclass{
  background-color: #f1f4f5;
  position: absolute;
  top:30%;
  width: 50%;
  left:25%;
  height: 180px;
  border-radius: 10px;
  line-height: 60px;
}
.refferbox{
  margin: 50px 0;
}
.reffertable_box{
  padding: 15px 0;
  background: #fdfbfb;
}
.reffertable{
  width: 100%;
  margin: 0 auto;
  font-size: 28px;
  border-radius: 10px;
  padding: 15px 0;
}
.reffertable tr td{
  width:25%;
}
.reffertable img{
  width:85%;
}

.reffertable p{
  margin:0;
  padding:0;
}
.closeclass{
  background-color: #f1e0e0
}

</style>