<template>
    <section class="app__container">
        <form class="app__container-form">
            <input v-model="name" class="app__form-input" placeholder="Timer Name">
            <button @click.prevent="add" class="app__form-btn">Create Timer</button>
        </form>
        <ul class="app__container-result">
            <li v-for="(item, index) in arrTimer" :key="index" class="app__result-item">
                <p class="app__item-name">{{item.title}}</p>
                <div class="app__items-connect">
                    <p class="app__item-time">
                        {{ item.timer | validateTime('hour') }}:{{ item.timer | validateTime('minute')}}:{{ item.timer | validateTime('second') }}
                    </p>
                    <div class="app__result-btns">
                        <button @click.prevent="start(item)" class="app__item-pause" :class="{'green': !item.worked}"><i class="material-icons" v-html="item.worked ? 'pause' : 'play_arrow'"></i></button>
                        <button @click.prevent="del(index)" class="app__item-delete"><i class="material-icons">delete</i></button>
                    </div>
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
        filters:{
            validateTime: function(value, timeUnit){
                switch (timeUnit){
                    case 'hour':
                        return 10 > Math.floor(value / 3600) ? '0' + Math.floor(value / 3600) : Math.floor(value / 3600)
                        break;
                    case 'minute':
                        return  10 > Math.floor((value % 3600) / 60) ? '0' + Math.floor((value % 3600) / 60) : Math.floor((value % 3600) / 60);
                        break;
                    case 'second':
                        return (10 > Math.floor(value % 3600) % 60) ? '0' + Math.floor(value % 3600) % 60 : Math.floor(value % 3600) % 60;
                        break; 
                }
            }
        },
        methods: {
            add: function(){
                let nameTemp = ''
                if(this.name == '') nameTemp = new Date().toISOString().slice(0, -14)
                else  nameTemp = this.name
                let obj = {
                    title: nameTemp,
                    timer: 0,
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
        },
        created: function () {
            window.addEventListener("unload", () => {
                localStorage.setItem('date', Date.parse(new Date()))
                localStorage.setItem('data', JSON.stringify(this.arrTimer))
            })
            try{
                if(JSON.parse(localStorage.getItem('data')) != null) this.arrTimer = JSON.parse(localStorage.getItem('data'))
                let range = (Date.parse(new Date()) - localStorage.getItem('date'))/1000
                this.arrTimer.forEach( (item, index) => {
                    if(item.worked){
                        item.timer = item.timer + range
                        item.worked = false
                        this.start(item)
                    }
                });
            }
            catch(err){
                console.log("Первый вход");
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
        display: flex;
        justify-content: center;
        padding: 40px 0;
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
        padding: 60px 0 0 0;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin: 0;
        list-style: none;
    }
    
    .app__items-connect{
        display: flex;
        justify-content: space-between;
    }

    .app__result-item{
        min-width: 420px;
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
        width: 80px;
        padding: 14px 24px;
        margin-right: 22px;
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
        margin: 0 0 0 20px;
        background: linear-gradient(135deg, #F23673 0%, #FCA069 100%);
        border-radius: 6px;
    }

    @media (max-width: 450px)  {
        .app__container-form{
            flex-direction: column-reverse;
            align-items: center;
        }

        .app__form-btn{
            margin: 0 0 20px 0;
        }

        .app__item-name{
            text-align: center;
        }
        .app__result-item, .app__items-connect{
            display: block;
        }
        .app__result-item{
            min-width: auto;
        }

        .app__item-time{
            margin: 25px 0;

        }
    }

</style>