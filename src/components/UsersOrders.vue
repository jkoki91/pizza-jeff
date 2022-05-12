<template>
    <div>
        <h1>Probando Orders</h1>
        <p>{{response}}</p>

        <!-- <b-card img-src="https://placekitten.com/1000/300" img-alt="Card image" img-top>
            <b-card-text>
                Some quick example text to build on the card and make up the bulk of the card's content.
            </b-card-text>
        </b-card> -->
    </div>
</template>

<script>
export default {
    data(){
        return{
            response: null,
            content: this.getUsers()

        }
    },
    watch:{
        
    },
    methods:{
        async getUsers() {
            await fetch('http://localhost:1907/orders').then(r=>r.json())
            .then(d=>{
                console.log(d.content)
                this.response = d.content
            })
        }
        
    },
    computed:{
        // content: this.getUsers()
    }
}
</script>

<style>

</style>