<template>
    <div class="small-pics" 
        :style="{top:(index%2)*31.48+'vh',
        left:(Math.floor(index/2))*17.708+'vw',
        transform:'scale('+size+')',
        boxShadow:shadow}"
        :size="change"
        :shadow="change"
        :new-url="parseUrl"
        :new-photo-name="parseName">   
        <img :src="newUrl">
        <pics-info class="pics-information"
         :big-size="bigSize" 
         :small-size="smallSize"
         :create-time="createTime" 
         :photo-name="newPhotoName" 
         :user-name="userName"
         :style="{display:display}"
         :display="change">
        </pics-info>
    </div>
</template>

<script>
    import bg1 from '../assets/favorite/visitedIcon.png'
    import PicsInfo from './PicsInfo'
    import router from '../router/index'
    export default {
        name: 'Collections',
        data() {
            return {
                size: 1,
                shadow: 'none',
                display: 'none',
                bigSize: 2.778,
                smallSize: 1.019,
                newUrl: "",
                newPhotoName: "",
            }
        },
        props: ['index', 'url', 'createTime', 'photoName', 'userName','counter'],
        components: {
            PicsInfo
        },
        methods: {
            
        },
        computed: {
            change: function (){
                if(this.counter===this.index+2){
                    this.size=1.133;
                    this.shadow = '0 6px 20px #222222';
                    this.display='block';
                }else{
                    this.size = 1;
                    this.shadow = 'none';
                    this.display = 'none';
                }
            },
            parseUrl: function (){
                this.newUrl = "http://39.108.149.106"+this.url;
            },
            parseName: function (){
                let str = "-";
                this.newPhotoName = this.photoName.split(str)[0];
            },
        }
    }
</script>
<style>
    .small-pics {
        width: 15.625vw;
        height: 27.78vh;
        position: absolute;
        transition: all 0.5s ease;
    }
    /* .small-pics:hover {
        transform: scale(1.133);
        position: absolute;
        box-shadow: 0 6px 20px #222222
    } */
    .small-pics>img {
        width: 100%;
        height: 100%;
    }
    .small-pics>.pics-information {
        width: 100%;
        height: 7.407vh;
        position: absolute;
        font-family: '小米兰亭';
        bottom: 0;
        left: 0;
        display: none;
        z-index: 2;
        transition: all 0.5s ease;
    }
    /* .small-pics:hover .pics-information {
        display: block;
    } */
</style>

