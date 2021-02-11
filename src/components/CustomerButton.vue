<template>
    <span class="block-button">
        <button @click="myFunction" class="block-button__customer">
            <slot>{{parameter.message}}</slot>
        </button>
    </span>
</template>

<script>
export default {
    props:{
        parameter: {
            type: Object,
            required: false,
            default: () =>(
                { 
                    message: 'pulsar'
                }
            )
        },
        callback:{
            type: Function,
            required: false
        }
    },
    methods:{
        myFunction(){
             if(this.callback && typeof this.callback==='function') 
                this.callback();
        }
    },
    // mounted(){
    //     this.callback(); 
    // }
}
</script>

<style lang="scss" scoped>
    .block-button__customer{
        padding: .6rem .8rem .8rem .8rem;
        border:1px solid skyblue;
        color: darken(skyblue,40);
        font-weight: bold;
        background-color: transparent;
        border-radius: .5rem;
        box-shadow: -1px -1px .1rem  inset black,
                    1px 1px .2rem  slategrey;
        cursor: pointer;
        transition: all ease .5s;
        outline-style: none;
        &:hover{
            transform: translateY(.2rem);
        }
        &:active{
            box-shadow: -1.6px -1.6px .1rem  inset black;
        }
    }
</style>