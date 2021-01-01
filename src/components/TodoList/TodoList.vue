<template>
    <div>
        <form @submit.prevent="updateToDoListItem">
            <input v-model.lazy="addItem" type="text" placeholder="Add your item" >
        </form>

        <br>

        <ul>
            <li v-for="(item, index) in items" :key="index"><button @click="removeItem(index)">Remove</button> Name : {{item.name}} => Price : <input type="text" v-model="item.price"></li>
            
        </ul>
        <p>Total : {{total}}</p>

        
    </div>
</template>

<script>
    export default {
        data() {
            return {
                items: [],
                addItem: ""
            }
        },
        methods: {
            updateToDoListItem(){
                this.items.push({
                    name: this.addItem,
                    price: 501
                })
                this.addItem = ""
            },
            removeItem(index){
                this.items.splice(index, 1)
            }
        },
        computed: {
            total(){
                let total = 0;
                for (const item of this.items) {
                    const price = item.price;
                    total += parseFloat(price);
                }
                return total;
            }
            
        }
    }
</script>

<style scoped>

</style>