<template>
	<div class="lunbo">
      <ul class="headpicul">
        <li v-for='(image,index) in img' :key='index' v-show='index==mark'>
          <img style="width:95%;border-radius: 7px;"  :src='image' @click="openDapp(index)"/>
        </li>
      </ul>
    </div>
</template>

<script>
	import Links from '../../common/links'
	import trans from '../../common/utils/trans'
	export default {
	  name: 'Head',
	  components: {},
	  data () {
	    return {
	    	mark:0,
      		img:[
      		'static/images/quake.png',
      		'static/images/atlantis.png']
	    };
	  },
	  mounted() {
	  	this.init()
	  },
	  updated:function(){
	  },
	  methods: {
	  	init:function(){
	  		window.setInterval(()=>{
	        this.autoPlay()
	      },3000)
	  	},
	  	autoPlay() {
		      this.mark++
		        if(this.mark === 2){
		          this.mark = 0 
		          return;
		        }
		  },
		 openDapp:function(index){
		 	// console.log(index)
		 	if(index==0){
		 		trans.$emit("tipsemit",{"name":"QUAKE","link":Links.url.quake,"state":0});
		 	}else if(index==1){
		 		trans.$emit("tipsemit",{"name":"Atlantis","link":Links.url.quake,"state":0});
		 	}
		 	
		 },
		 linkx:function(name,link){
		 	  let dname = window.localStorage.getItem(name);
		      if(dname){
		        window.open(link,'_self')
		      }else{
		        trans.$emit("tipsemit",{"name":name,"link":link});
		      }
		 }
	  }
	}

</script>

<style scoped>
.lunbo{
	margin-top: 60px;
}
.headpicul{
  list-style: none;
  padding:0;
  margin:0;
}
</style>