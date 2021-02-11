<template> 
    <component :is="getType" :href="href"  @click="myFunction($event)" class="my-button">
        <slot>{{message}}</slot>
    </component>    
</template>

<script>
export default {
    props:{
       message:{
           type: String,
           default: 'Pulsar',
           required: false
       },
       href:{
           type: String,
           default:null,
           required: false
       },
       callback:{
            type: Function,
            required: false        
        }
    },
    computed:{
       getType(){
           return this.href?"a":"button";
       } 
    },
    methods:{
        myFunction(e){
             
             if(this.callback && typeof this.callback==='function') 
                this.callback(e);
        }
    }
}
</script>

<style lang="scss" scoped>
    button.my-button,a.my-button{
        display: inline-block;
        padding: .6rem .8rem .8rem .8rem;
        border:1px solid skyblue;
        color: darken(skyblue,40);
        font-size: 1rem;
        text-decoration: none;
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