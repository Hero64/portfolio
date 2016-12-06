<template>
    <div class="detail" :class="enable">
        <button class="close-btn" @click="close">
            <span></span>
            <span></span>
        </button>
        <img :src="information.big_image" class="img-responsive">
        <div class="detail-content" >
            <h3>{{ information.title }}</h3>
            <p>{{ information.description }}</p>
            <h4>Vinculos</h4>
            <ul class="list-unstyled">
                <li v-for="link in information.url">
                    <a :href="link" target="_blank">{{ link }}</a>
                </li>
            </ul>
        </div>
    </div>
</template>
<style>
    .detail {
        position: fixed;
        top: 0;
        right: -100%;
        width: 450px;
        height: 100%;
        z-index: 2;
        background: #333;
        box-shadow: 0 0 5px #333;
        transition: .6s;
    }
    .detail.active {
        right: 0%;
    }
    .detail h4 {
        margin-bottom: 15px;
        padding-bottom: 15px;
        border-bottom: 2px solid #fff;
    }
    .detail-content {
        position: relative;
        min-height: 300px;
        box-shadow: -1px -41px 74px #333;
        color: #fff;
        padding: 25px;
    }
    .detail-content::before {
        content: '';
        height: 65px;
        width: 100%;
        left: 0;
        bottom: 100%;
        background: -moz-linear-gradient(top, rgba(51,51,51,0) 0%, rgba(51,51,51,0.01) 1%, rgba(51,51,51,1) 100%); /* FF3.6-15 */
        background: -webkit-linear-gradient(top, rgba(51,51,51,0) 0%,rgba(51,51,51,0.01) 1%,rgba(51,51,51,1) 100%); /* Chrome10-25,Safari5.1-6 */
        background: linear-gradient(to bottom, rgba(51,51,51,0) 0%,rgba(51,51,51,0.01) 1%,rgba(51,51,51,1) 100%); /* W3C, IE10+, FF16+, Chrome26+, Opera12+, Safari7+ */
        filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#00333333', endColorstr='#333333',GradientType=0 );
        position: absolute;
    }
    .close-btn {
        padding: 0;
        cursor: pointer;
        background: 0 0;
        border: 0;
        height: 30px;
        width: 30px;
        z-index: 3;
        position: absolute;
        top: 15px;
        left: 15px;
        outline: none;
    }
    .close-btn span {
        width: 100%;
        display: block;
        height: 3px;
        margin-bottom: 5px;
        background: #fff;
        box-shadow: 0 0 1px #000;
        position: relative;
    }
    .close-btn span:first-child {
        transform: rotate(45deg);
        top: 8px;
    }
    .close-btn span:last-child {
        transform: rotate(-45deg)
    }
</style>
<script>
    export default{
        data: function() {
            return {
                enable: {
                    active: false
                },
                information: {
                }
            }
        },
        methods: {
            close: function() {
                this.setActive(false);
            },
            setInformation: function(data) {
                this.information = data;
            },
            setActive: function(active) {
                this.enable.active = active;
            }
        }
    }
</script>
