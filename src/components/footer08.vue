<template>
    <div class="footer">
        <ul>
            <li>
                <router-link :to="{ name: 'Index', params:{rname:'首页'}}" v-bind:class="{ active:isMore01 }">
                    <i class="iconfont icon-home01"></i>
                    <p>首页</p>
                </router-link>
             </li>
            <li>
                <router-link :to="{ name: 'news', params:{rname:'综合新闻'}}" v-bind:class="{ active: isNews }">
                    <i class="iconfont icon-news"></i>
                   <p>综合新闻</p>
                </router-link>
            </li>
           <li >
                <router-link :to="{ name: 'htmlViewSample', params:{rname:'赛程赛事'}}">
                    <i class="iconfont icon-ball01 f22"></i>
                   <p>赛程赛事</p>
                </router-link>
            </li>
            <li>
                <router-link :to="{ name: 'vip', params:{rname:'会员中心'}}"  v-bind:class="{ active: isActive }">
                    <i class="iconfont icon-user02 f20"></i>
                   <p>会员中心</p>
                </router-link>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
  name: 'App',
  data(){  
        return{  
            isActive: false,
            isNews: false,
            isMore01: true,
        }  
    },
  　watch: {
　　　'$route' (to, from) {
       var isBack = this.$router.isBack; // 监听路由变化时的状态为前进还是后退
　　　　　　if(isBack) {
　　　　　　　this.transitionName = 'slide-right';
　　　　　　} else {
　　　　　　 this.transitionName = 'slide-left';
　　　　　}
　　    this.$router.isBack = false;
　　},
    $route(to,from){
        if(to.path == '/feedback' || to.path == '/disclaimer' || to.path == '/message' || to.path == '/favorites' || to.path == '/fans' || to.path == '/follow'){ //用户中心
            this.isActive = true;
            this.isBanner = false;
        }else{
            this.isActive = false;
            this.isBanner = false;
        }
        if(to.path == '/'){ //用户中心
            this.isMore01 = true;
        }else{
            this.isMore01 = false;
        }
        if(to.path == '/newsMore' || to.path == '/newsMore1' || to.path == '/newlists1' || to.path == '/newlists2' || to.path == '/newlists3' || to.path == '/newlists4' || to.path == '/newlists5' || to.path == '/newlists6' || to.path == '/newlists7' || to.path == ' framekj'){ //新闻中心
            this.isNews = true;
            this.isBanner = false;
        }else{
            this.isNews = false;
            this.isBanner = true;
        }
        if(to.path != from.path){ //滚动条置顶
            document.getElementById('vrw').scrollTop = 0;
        }
        
    },
　 }
}
</script>
<style lang="scss" scoped>
@import "scss/base.scss";
.footer{
    position: fixed;
    bottom:-1px;
    left:0px;
    display: block;
    width: 100%;
    border-top:1px solid #dddddd
}
.footer ul{
    width: 100%;
}
.footer ul li{
    float:left;
    width:25%;
}
// .footer ul li:nth-child(2){
//     float:left;
//     width:34%;
// }
.footer ul li a{
    text-align: center;
    background: #d43b33;
    color:#ffa803;
    height: 0.45rem;
    display: inherit;
    padding-top: 0.01rem;
    font-size: 0.2rem;
    border-bottom: 1px solid #fff;
    width: 100%;
}
.footer ul li i{
    width: 100%;
    line-height: 0.24rem;
    font-size: 0.24rem;
    padding-top:0.04rem;
    float:left;
}
.f20{
    font-size: 0.2rem!important;
}
.f22{
    font-size: 0.22rem!important;
}
.footer ul li p{
    width: 100%;
    line-height: 0.15rem;
    float:left;
    text-align: center;
    margin-top:0.02rem;
}
.footer ul li .router-link-exact-active{
    border-bottom:1px solid #fff;
    color:#fff;
}

.footer .active{
    border-bottom:1px solid #fff;
    color:#fff;
}

</style>