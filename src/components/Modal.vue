<template>
<!-- we want click happend just on backdrop not the child , so we use click event modifier(.self)-->
    <div class="backdrop" @click.self="closeModal">
        <div class="modal">
            <h1>{{header}}</h1>
            <p>{{text}}</p>
            <slot></slot>
            <!-- output name slot with name tag-->
            <div class="actions">
                <slot name="links"></slot>
            </div>
        </div>
    </div>
</template>

<script>


export default{
    props: ['header', 'text', 'theme'],
    methods: {
        closeModal(){
            // custome event
            this.$emit('close')
        }
    }
}
</script>


<style>
    .modal{
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background: #fff;
        border-radius: 10px;
    }
    .backdrop{
        top: 0;
        position: fixed;
        background: #000;
        opacity: .8;
        width: 100%;
        height: 100%;
    }
    .modal .actions{
        text-align: center;        
    }
</style>