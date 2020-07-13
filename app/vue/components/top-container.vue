<template>
    <header class="header">
        <div class="header__wrapper">
            <nav class="nav__container">
                <p class="nav__title">AppStarter</p>
                <ul class="nav__items">
                    <li class="nav__item"><a href="#">Features</a></li>
                    <li class="nav__item"><a href="#">Video Tour</a></li>
                    <li class="nav__item"><a href="#">Reviews</a></li>
                    <li class="nav__item"><a href="#">Pricing</a></li>
                    <li class="nav__item-btn"><button>GET IT FREE</button></li>
                </ul>
            </nav>
            <div class="header__inner">
                <div class="inner__intro">
                    <div class="header__inner-icon"></div>
                    <p class="inner__intro-title"><strong>AppStarter.</strong> Best landing page for web and mobile apps </p>
                    <button class="inner__intro-download">Download Now</button>
                    <button class="inner__intro-watch">Watch Video</button>
                </div>
                <div class="inner__tablet">
                    <div class="tablet__pic"></div>
                </div>
            </div>
        </div>
    </header>
</template>

<script>
    module.exports = {
        data: function (){
            return {
                
            }
        },
    }
</script>

<style scoped>
    .header{
        max-width: 100%;
        height: 900px;
        background: url('../images/header__background.png') no-repeat;
    }

    .header__wrapper{
        padding: 25px 135px 0;
    }

    .nav__container{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .nav__title{
        font-size: 20px;
        color: #fff;
    }

    .nav__items{
        display: flex;
        align-items: center;
        list-style: none;
    }

    .nav__item{
        padding-right: 30px;
    }

    .nav__item-btn button{
        width: 130px;
        height: 40px;
        font-size: 14px;
        font-weight: bold;
        border-radius: 6px;
        border: none;
        color: #282B31;
        background: #fff;
    }

    .nav__item a{
        font-size: 15px;
        text-decoration: none;
        color: #fff;
    }

    .header__inner-icon{
        width: 90px;
        height: 90px;
        background: url('../images/header__app-icon.png');
        border-radius: 20px;
    }

    .header__inner{
        display: flex;
        justify-content: space-between;
        padding: 75px 0;
    }

    .inner__intro{
        padding: 165px 0;
        width: 555px;
    }

    .inner__intro-title{
        margin: 33px 0 37px 0;
        font-size: 35px;
        line-height: 50px;
        color: #fff;
    }

    .inner__intro-title strong{
        font-weight: 800;
    }

    .inner__intro-download{
        width: 167px;
        height: 50px;
        margin-right: 20px;
        border: none;
        background: linear-gradient(163.33deg, #FF8E64 0%, #FFE641 100%);
        border-radius: 6px;
        font-size: 17px;
        color: #fff;
    }

    .inner__intro-watch{
        width: 144px;
        height: 50px;
        border-radius: 6px;
        font-size: 17px;
        border: none;
        color: #282B31;
    }

    .inner__tablet{
        min-width: 470px;
        height: 700px;
        border-radius: 50px;
        background: #fff;
    }

    .tablet__pic{
        background: url('../images/tablet__background.png') no-repeat center;
        width: 100%;
        height: 100%;
    }

</style>