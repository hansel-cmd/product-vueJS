<template>
<div class="rightsection">

        <div class="products">
            <table class="header">
                <tr>
                    <th> ID </th>
                    <th> Product Name </th>
                    <th> Category </th>
                </tr>
                <tr v-bind:id="item.id" class="cat" v-for="item in products" v-bind:key="item.id">
                    <td> {{ item.id }} </td>
                    <td> {{ item.productName }} </td>
                    <td>
                        |
                        <span v-for="cat in item.category" v-bind:key="cat">
                            {{ cat + ' | ' }}
                        </span>
                    </td>
                </tr>
            </table>
        </div>
    </div>
</template>


<script>
export default {
    name: 'Right-Section',
    props: {
        products: {
            type: Array
        }
    },
}
</script>