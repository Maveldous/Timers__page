<template>
    <section class="app__container">
        <form class="app__container-form">
            <input v-model="name" class="app__form-input" placeholder="Timer Name">
            <button @click.prevent="add" class="app__form-btn">Create Timer</button>
        </form>
        <ul class="app__container-result">
            <li v-for="(item, index) in arrTimer" :key="index" class="app__result-item" >
                <p class="app__item-name">{{item.title}}</p>
                <p class="app__item-time">
                    {{ 10 > Math.floor(item.timer / 3600) ? '0' + Math.floor(item.timer / 3600) : Math.floor(item.timer / 3600) }}:{{ 10 > Math.floor((item.timer % 3600) / 60) ? '0' + Math.floor((item.timer % 3600) / 60) : Math.floor((item.timer % 3600) / 60)}}:{{ (10 > Math.floor(item.timer % 3600) % 60) ? '0' + Math.floor(item.timer % 3600) % 60 : Math.floor(item.timer % 3600) % 60 }}
                </p>
                <div class="app__result-btns">
                    <button @click.prevent="start(item)" class="app__item-pause" :class="{'green': !item.worked}"><i class="material-icons" v-html="item.worked ? 'pause' : 'play_arrow'"></i></button>
                    <button @click.prevent="del(index)" class="app__item-delete"><i class="material-icons">delete</i></button>
                </div>
            </li>
        </ul>
    </section>
</template>

<script>
    module.exports = {
        data: function (){
            return {
                arrTimer: [],
                name: ''
            }
        },
        methods: {
            add: function(){
                let nameTemp = ''
                if(this.name == '') nameTemp = new Date().toISOString().slice(0, -14)
                else  nameTemp = this.name
                let obj = {
                    title: nameTemp,
                    timer: 3673,
                    worked: false,
                    interval: ''
                }
                this.arrTimer.unshift(obj)
                this.name = ''
                this.start(this.arrTimer[0])
            },
            start: function(value){
                if(!value.worked){
                    value.interval = setInterval(() => {
                        value.timer++
                    }, 1000)
                    value.worked = true
                }
                else{
                    clearInterval(value.interval)
                    value.worked = false
                }
            },
            del: function(value){
                this.arrTimer.splice(value, 1)
            }
        }
    }
</script>

<style scoped>
    .app__container{
        max-width: 770px;
        margin: 0 auto;
        padding: 60px 0 113px 0;
    }
    .app__container-form{
        padding: 40px 140px;
        display: flex;
    }

    .app__form-input{
        width: 305px;
        height: 50px;
        font-size: 17px;
        line-height: 23px;
        border: none;
        padding-left: 20px;
    }

    .app__form-btn{
        width: 165px;
        height: 50px;
        font-size: 17px;
        line-height: 24px;
        color: #FFFFFF;
        background: linear-gradient(163.14deg, #FF8E64 0%, #FFE641 100%);
        border-radius: 6px;
        border: none;
        margin-left: 20px;
    }

    .app__container-result{
        padding: 60px 140px 0;
        margin: 0;
        list-style: none;
    }
    
    .app__result-item{
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding-bottom: 40px;
    }

    .app__item-name{
        max-width: 120px;
        word-wrap: break-word;
        font-size: 20px;
        color: #5586F2;
    }

    .app__item-time{
        width: 60px;
        padding: 14px 24px;
        font-size: 17px;
        color: #676C75;
        background: #E7E8EA;
        border-radius: 6px;
        border: none;
    }

    .app__item-pause, .app__item-delete{
        height: 50px;
        width: 50px;
        border: none;
    }

    .app__item-pause{
        background: linear-gradient(135deg, #7956EC 0%, #2FB9F8 100%);
        border-radius: 25px;
    }

    .app__item-pause.green{
        background: linear-gradient(135deg, #009FC5 0%, #3CECB0 100%);
    }

    .material-icons{
        color: #fff;
    }

    .app__item-delete{
        margin: 0 20px;
        background: linear-gradient(135deg, #F23673 0%, #FCA069 100%);
        border-radius: 6px;
    }



    /* .material-icons::before{
        font-family: "Material Design Icons";
        position: absolute;
        content: '\F01C9';
        width: 100px;
        height: 100px;
        
    } */

</style>