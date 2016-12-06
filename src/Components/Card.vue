<template>
    <div class="col-md-4 col-sm-6 col-xs-12">
        <div class="card">
            <img :src="card.image" class="img-responsive">
            <div class="description">

                <h3>{{ card.title }}</h3>
                <p></p>
                <a href="#" @click.prevent="showDetail()">Ver detalle</a>
            </div>
        </div>
    </div>
</template>
<style lang="css">
    .card {
        border: 2px solid #333;
        position: relative;
        overflow: hidden;
        margin-bottom: 25px;
    }
    .card > .description  {
        border-top: 2px solid #333;
        padding: 15px 15px 45px 15px;
        color: #fff;
        background: #333;
        position: relative;
    }
    .card > img {
        width: 100%;
    }
    .card  > .description::before {
        content: '';
        height: 45px;
        width: 104%;
        background: #333;
        transform: rotate(-5deg);
        top: -25px;
        left: -5px;
        position: absolute;
        transition: .4s;
    }
    .card:hover > .description::before {
        top: -45px;
        height: 65px;
    }
    .card > .description a {
        text-decoration: none;
        text-align: right;
        display: block;
        color: #fff;
    }

</style>
<script>
    export default {
        props: ['card', 'random-class'],
        methods: {
            showDetail: function() {
                console.log(this);
                this.$parent.$refs.detail.setInformation(this.card);
                this.$parent.$refs.detail.setActive(true);

            }
        }
    }
</script>
