<script>
import AppHeader from "@/components/AppHeader.vue";
import AppFooter  from "@/components/AppFooter.vue"
export default {
	components: {
		AppHeader,
        AppFooter
	},
};
</script>

<template>
	<div id="app">
		<AppHeader />

		<div >
			<router-view />
		</div>
        <AppFooter/>
	</div>
</template>

<style>

.modal {
  padding-right: 0px !important;
}
  .container-fluid{
    padding:0;
    animation: grow linear  0.8s ;
  }
  .lSPager {
    margin-top: 5px;
    position: absolute;
    top: 75%;
    right: 46%;
  }
  
  .banner-first{
    position: relative;
    animation: grow linear  0.8s ;
    
  }
  .banner-second,
  .banner-first-img,
  .body__heading-img{
    width:100%;
    height:486px;
    flex-wrap: wrap;
  }
  .banner-first-btn{
    position: absolute;
    bottom: 14%;
    width: 250px;
    height: 40px;
    font-size:18px;
    right: 19%;
    border: 1px solid rgb(243, 189, 122);
    color: rgb(243, 189, 122);
    line-height: 17px;
    animation: btn-linear linear  0.8s
  }
  .btn2{
    left: 13%;
    /* boot: 80%; */
    z-index: 10;
    animation: btn-linear linear  0.8s
  }
  .banner-second-left{
    width: 100%;
    height:100%;
     background-size: cover;
    background-image: url(https://www.highlandscoffee.com.vn/vnt_upload/weblink/homepage-STORE_1.jpg)  ;
    background-repeat: no-repeat, repeat;
  }
  .banner-second-right{
    padding: 0;
    width: 100%;
    height:100%;
    background-image: url(https://www.highlandscoffee.com.vn/vnt_upload/weblink/bg2.jpg);
    background-repeat:  repeat;
  }
  	
  .banner-first-btn:hover{
    color: black;
    background: rgb(243, 189, 122);
  
  }
  .banner-second-left-item{
    color: white;
  }
  .banner-second-left-text{
    font-size:24px;
    font-weight: 700;
  }
  .banner-second-left-description{
    padding-top: 12px;
    font-size:18px;
    font-weight: 700;
  }
  .address{
    font-size:36px; color: white; font-weight: 700; padding-top:10%;
  }
  
  .banner-second-right-items{
    padding-left: 100px;
    list-style:none;
    padding-top:50px;
  }
  .banner-second-right-item-header{
    height:40px;
    width: 500px;
    display:flex;
    justify-content: space-between;
  }
  .banner-second-right-item{
    width: 500px;
    display:flex;
  }
  .banner-second-right-img{
    width:120px;
    height:67px;
  }
  
  .banner-second-right-header{
    font-size:24px;
    font-weight: 700;
  }
  .banner-second-right-body{
    padding-left: 0;
  }
  
  .banner-second-right-text{
    font-size:18px;
    margin-bottom: 6px;
  }
  .banner-second-right-calendar{
    font-size:14px;
    padding-left: 4px;
  }
  .banner-second-right-link{
    color:black;
    font-size:16px;
  }
  .btn-submit{
    background-color:#53382c;
    color: white;
  }
  @keyframes grow {
      0%{
        opacity:0;
      }
      100%{
        opacity:1;
      }
  }
  @keyframes btn-linear {
    0%{
      opacity:1;
      bottom: 5%;
    }
    100%{
      opacity:0;
      bottom: 14%;
    }
  }
  @keyframes btn-linear {
    0%{
      opacity:1;
      top: 80%;
    }
    100%{
      opacity:0;
      top: 70%;
    }
  }
@media only screen and (min-width:768px) and (max-width:1023px){
    .banner-first-img,
    .body__heading-img{
    /*width:100%;*/
    /*height:245px;*/
    }
     .banner-second{
      height:100%;
    }
 }
  @media (max-width:767px){
    .banner-first-img,
    .body__heading-img{
    width:100%;
    height:132px;
    }
    .banner-first-btn{
      display: none ;
    }
    .lSPager {
    display: none
    }
    .banner-second{
      height:100%;
    }
    .banner-second-right-items{
      padding:0;
    }
    .banner-second-right-item{
      width: 100%;
      display:flex;
      padding:6px;
    }
    .banner-second-right-body{
      padding-left:18px;
    }
    .banner-second-right-item-header{
      padding:12px 0px 24px 12px;
      width: 100%;
    }
  }
  

</style>
