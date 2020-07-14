<template>
    <section class="bottom__container">
        <div class="bottom__container-wrapper">
            <p class="bottom__container-title"><strong>Why</strong> do we use it?</p>
            <p class="bottom__container-text">This sounded nonsense to Alice, so she said nothing, but set off at once toward the Red Queen. To her surprise, she lost sight of her in a moment.</p>
            <app-component></app-component>
            <footer class="footer">
                <div class="footer__wrapper">
                    <p class="footer__wrapper-text">AppStarter</p>
                    <div class="footer__wrapper-textblock">
                        <p class="footer__wrapper-text2">Created with </p> <img class="heart__icon" src="../images/heart__icon.png" alt="heart__icon"><p class="footer__wrapper-text2"> by <strong> Sergey Azovskiy</strong></p>
                        <p class="footer__bottom-text">© AppStarter, 2017</p>
                    </div>
                    <ul class="footer__icons">
                        <li class="footer__icon"><a href="#"><img src="../images/twitter__icon.png" alt="twitter__icon"></a></li>
                        <li class="footer__icon"><a href="#"><img src="../images/facebook__icon.png" alt="facebook__icon"></a></li>
                        <li class="footer__icon"><a href="#"><img src="../images/instagram__icon.png" alt="instagram__icon"></a></li>
                    </ul>
                </div>
            </footer>
        </div>
    </section>
</template>


<script>
    module.exports = {
        data: function (){
            return {}
        },
        components: {
            'app-component': require('./app-component.vue')
        }
    }
</script>

<style scoped>
    .bottom__container-wrapper{
        height: 100%;
    }

    .bottom__container-title{
        font-size: 35px;
        text-align: center;
        padding-bottom: 17px;
        color: #282B31;
    }
    .bottom__container-text{
        max-width: 570px;
        margin: 0 auto;
        text-align: center;
        color: #676C75;
    }
    .footer__wrapper{
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0px 135px;
    }

    .footer__wrapper-text{
        font-weight: 800;
        font-size: 20px;
        color: #282B31;
    }

    .footer__wrapper-textblock{
        margin: 20px 0 0 0;
    }

    .footer__wrapper-text2, .footer__bottom-text{
        padding-bottom: 10px;
        font-size: 11px;
        color: #999EA8;
    }

    .heart__icon, .footer__wrapper-text2{
        display: inline;
    }

    strong{
        color: #282B31;
    }

    .footer__bottom-text{
        text-align: center;
    }

    .footer__icon{
        position: relative;
        display: inline-block;
        height: 40px;
        width: 40px;
        text-align: center;
    }
    .footer__icon img{
        margin-top: 12px;
    }

    @media (max-width: 700px) {
        .footer__wrapper{
            padding: 0;
        }
    }

    @media (max-width: 500px) {
        .footer__icon{
            height: 20px;
            width: 20px;
        }
        .footer__wrapper-text2, .footer__bottom-text{
            font-size: 7px;
        }
    }

</style>