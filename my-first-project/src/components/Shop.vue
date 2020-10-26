<template>
    <div>
        <h1>{{ shopTitle }}</h1>
        <div v-for="(phone, key) in phones" :key="key" class="card">
            <h4>{{ phone.title }}</h4>
            <div>
                <button class="btn" v-on:click="minusCount(phone)">-</button>
                <input v-model="phone.count" type="text" class="input">
                <button class="btn" @click="plusCount(phone)">+</button>
            </div>
            <div>{{ itemPrice(phone) }} руб.</div>
        </div>
        <div>Сумма: {{ totalPrice }}</div>        
    </div>
</template>

<script>
    export default {
        name: "Shop.vue",
        props: {
            shopTitle: String,
        },
        data () {
            return {
                phones: [
                    {
                        title: "Apple iPhone X",
                        price: 70000,
                        count: 0,
                    },

                    {
                        title: "Huawei Honor 10",
                        price: 15000,
                        count: 0,
                    },

                    {
                        title: "Samsung Galaxy Flip2",
                        price: 189000,
                        count: 0,
                    },

                    {
                        title: "One Plus One",
                        price: 10000,
                        count: 0,
                    },
                ] 
            }
        },
        computed: {
            totalPrice() {
                let sum = 0;
                this.phones.forEach(phone => {
                    sum += phone.count * phone.price;
                });
                return sum
            }
        },
        methods: {
            itemPrice(phone) {
                return +phone.count !== 0 ? phone.count * phone.price : phone.price
            },
            plusCount(phone) {
                phone.count = +phone.count + 1;
            },
            minusCount(phone) {
                //phone.count = +phone.count - 1;
                phone.count = +phone.count <= 0 ? 0 : +phone.count - 1;
            },
        }

    }
</script>

<style scoped lang="scss">

.card {
    box-shadow: 0 2px 1px #333;
    border-radius: 8px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 5px 20px;
    margin-bottom: 10px;
}

.btn {
    box-shadow: none;
    border: 1px solid #ccc;
    background: #ffffff;
    height: 30px;
    width: 30px;
    cursor: pointer;

    &:first-child {
        border-radius: 8px 0px 0px 8px;

        &:hover {
            background: red;
            color: #fff;
        }
    }

    &:last-child {
        border-radius: 0px 8px 8px 0px;

        &:hover {
            background: green;
            color: #fff;
        }
    }
}

.input {
    box-sizing: border-box;
    height: 30px;
    border: 1px solid #ccc;
    border-left: 0;
    border-right: 0;
    width: 30px;
    text-align: center;
}
</style>