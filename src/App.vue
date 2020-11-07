<template>
<div id="app">
    <header-app v-on:filter-items="filterItems"></header-app>
    <br /><br /><br /><br />
    <div class="mainpage">
        <left-section v-on:clicked-categories="checkItems($event)"></left-section>
        <right-section v-bind:products="filtered"></right-section>
    </div>
</div>
</template>



<script>
import headerapp from './components/Header-App.vue';
import leftsection from './components/Left-Section.vue';
import rightsection from './components/Right-Section.vue';


export default {
  name: "App",
  components: {
    'header-app': headerapp,
    'left-section': leftsection,
    'right-section': rightsection
  },
  data() {
    return {
      // not null, otherwise we cant see anything
      clickedCategory: ['Meat', 'Seafood', 'Fresh', 'Poultry', 'Sauce', 'Seasoning', 'Utensils', 'Cookware', 'Dairy', 'Fresh'],
      searchItem: "",
      items: [{
                    id: 1,
                    productName: 'Bacon',
                    category: ['Meat']
                },
                {
                    id: 2,
                    productName: 'Fish',
                    category: ['Seafood', 'Fresh']
                },
                {
                    id: 3,
                    productName: 'Chicken',
                    category: ['Poultry', 'Fresh']
                },
                {
                    id: 4,
                    productName: 'Beef',
                    category: ['Meat']
                },
                {
                    id: 5,
                    productName: 'Soy Sauce',
                    category: ['Sauce', 'Seasoning']
                },
                {
                    id: 6,
                    productName: 'Milk',
                    category: ['Dairy']
                },
                {
                    id: 7,
                    productName: 'Cheese',
                    category: ['Dairy']
                },
                {
                    id: 8,
                    productName: 'Frying Pan',
                    category: ['Utensils', 'Cookware']
                },
                {
                    id: 9,
                    productName: 'Egg',
                    category: ['Dairy']
                },
                {
                    id: 10,
                    productName: 'Plates',
                    category: ['Utensils']
                },
                {
                    id: 11,
                    productName: 'Pork',
                    category: ['Meat']
                },
            ],
      incaseEmpty: [{
                    id: 1,
                    productName: 'Bacon',
                    category: ['Meat']
                },
                {
                    id: 2,
                    productName: 'Fish',
                    category: ['Seafood', 'Fresh']
                },
                {
                    id: 3,
                    productName: 'Chicken',
                    category: ['Poultry', 'Fresh']
                },
                {
                    id: 4,
                    productName: 'Beef',
                    category: ['Meat']
                },
                {
                    id: 5,
                    productName: 'Soy Sauce',
                    category: ['Sauce', 'Seasoning']
                },
                {
                    id: 6,
                    productName: 'Milk',
                    category: ['Dairy']
                },
                {
                    id: 7,
                    productName: 'Cheese',
                    category: ['Dairy']
                },
                {
                    id: 8,
                    productName: 'Frying Pan',
                    category: ['Utensils', 'Cookware']
                },
                {
                    id: 9,
                    productName: 'Egg',
                    category: ['Dairy']
                },
                {
                    id: 10,
                    productName: 'Plates',
                    category: ['Utensils']
                },
                {
                    id: 11,
                    productName: 'Pork',
                    category: ['Meat']
                },
            ],
    }
  },
  methods: {
    // we put the header-app's event here because if it's computed,
    // it throws an error. Just use another variable and then use that inside computed
    filterItems(e) {
      this.searchItem = e;
      console.log(this.searchItem);
    },
    checkItems(e) {
      this.clickedCategory = e;
    }

  },
  computed: {
    filtered() {
      // temp and prod are just temp arrays we use to traverse
      // tag filtered = output 
      let temp = this.clickedCategory;
      let prod = this.items;
      let tagFiltered = [];

      prod.forEach(item => {
        for (let i = 0; i < temp.length; i++) {
          // break, so no duplicates
          if (item.category.includes(temp[i])) {
            tagFiltered.push(item);
            break;
          }
        }
      });
      
      // meaning, we filter by tag
      if (this.searchItem == "") {
        console.log(tagFiltered.length);
        return tagFiltered.length != 0 ? tagFiltered : this.incaseEmpty;
      }

      // filter by search input
      let x = this.items.filter(item => {
        return item.productName.toUpperCase().match(this.searchItem.toUpperCase());
      });

      x = new Set(x);
      x = [...x];

    
      return x;
    }
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Ubuntu:wght@700&display=swap');

#app {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}

body {
    font-family: arial;
    background: #3f3f3f;
}

.upperbar{
	background-color:#41B883;
	position: fixed;
	top: 0px; 
	display: flex;
	justify-content: flex-end;
	width: 100%;
	box-sizing: border-box;
	z-index: 1;
	padding: 0px 20px;
	left: 0px;
}

.title{
	margin-right: 15%;
	float: left;
	padding-left: 2%;
}

.title h1{
	text-align: left;
	font-family: 'Ubuntu', sans-serif;
}

.searchbar{
	position: relative;
	min-width:150px;
	width: 30%;
	top: 20px;
	float: right;
	overflow: hidden;
}

.searchbar input{
	overflow: hidden;
	display: flex;
	position: relative;
	height:40px;
	min-width:100px;
	width: 100%;
	padding-left: 5px;
}

.searchbar input:focus {
  outline: none;
}

.mainpage {
    max-width: 90%;
    width: 90%;
    margin: 0 auto;
    display: flex;
    height: auto;

}

label {
    text-align: left;
    margin: 20px 0px;
}

.leftsection div {
    font-size: 25px;
    text-align: center;
    width: 100%;
    margin-bottom: 13%;
}

.leftsection {
    padding-top: 3%;
    background-color: #4FDF9F;
    box-sizing: border-box;
    position: relative;
    width: 25%;
}

.leftsection .flex {
    display: flex;
    flex-direction: column;
    width: 100%;
}

.leftsection .flex label,
.leftsection .flex {
    margin-top: 0px;
    margin-bottom: 0px;
    margin-left: 10%;
}

.leftsection input {
    cursor: pointer;
    min-height: 5px;
    min-width: 5px;
    height: 20px;
    width: 20px;

    position: relative;
}

.rightsection {
    background-color: #41B883;
    position: relative;
    float: right;
    width: 75%;
    padding-bottom: 3%;
    box-sizing: border-box;
    height: auto;
}

.items {
    margin-left: 2%;
    margin-right: 2%;
}

.products {
  margin: 20px;
}

table {
    width: 100%;
    align-content: center;
    align-items: center;
    border-collapse: collapse;
}

td:first-child {
    font-weight: bold;
}

tr {
    position: relative;
    text-align: center;
    background-color: #86ffc6;
    padding: 5%;
}

.hide {
  display: none;
}

.cat:hover {
    background-color: #1b9c75;
    cursor: pointer;
}

th {
    border: 1px solid #000000;
    padding: 10px;
    height: 50px;
    align-content: center;
    background-color: #4FDF9F;
}

.header {
    margin-bottom: 5px;
    margin-top: 2%;
    background-color: #FFAE36;
}

td {
    border: 1px solid #000000;
    padding: 10px;
    height: 40px;
    text-align: center;
}
</style>
