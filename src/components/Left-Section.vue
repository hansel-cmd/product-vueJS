<template>
 <div class="leftsection">
        <div style="font-weight: bold;">Tags<br>
        </div>
        <div class="flex">
            <label> <input type="checkbox" value="Meat" v-model="categories" v-on:change="click"> Meat </label>
            <br />
            <label> <input type="checkbox" value="Seafood" v-model="categories" v-on:change="click"> Seafood </label>
            <br />
            <label> <input type="checkbox" value="Fresh" v-model="categories" v-on:change="click"> Fresh </label>
            <br />
            <label> <input type="checkbox" value="Poultry" v-model="categories" v-on:change="click"> Poultry </label>
            <br />
            <label> <input type="checkbox" value="Sauce" v-model="categories" v-on:change="click"> Sauce </label>
            <br />
            <label> <input type="checkbox" value="Seasoning" v-model="categories" v-on:change="click"> Seasoning </label>
            <br />
            <label> <input type="checkbox" value="Dairy" v-model="categories" v-on:change="click"> Dairy </label>
            <br />
            <label> <input type="checkbox" value="Utensils" v-model="categories" v-on:change="click"> Utensil </label>
            <br />
            <label> <input type="checkbox" value="Cookware" v-model="categories" v-on:change="click"> Cookware </label>
            <br />
        </div>
    </div>
</template>

<script>
export default {
    name: 'Left-Section',
    data() {
        return {
            categories: []
        }
    },
    methods: {
        click() {
            let arr = [...this.categories];
            // console.log(arr);
            this.$emit('clicked-categories', arr);
        }
    }

};
</script>

