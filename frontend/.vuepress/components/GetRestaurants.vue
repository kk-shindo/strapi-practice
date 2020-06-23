<template>
    <div>
        <h2>Restaurants</h2>
        <table class="table">
            <tr v-for="restaurant in restaurants">
                <th>id</th>
                <th>name</th>
                <th>description</th>
                <th>created_at</th>
                <th>updated_at</th>
                <th>categories</th>
            </tr>
            <tr v-for="restaurant in restaurants">
                <td>{{ restaurant.id }}</td>
                <td>{{ restaurant.name }}</td>
                <td>{{ restaurant.description }}</td>
                <td>{{ restaurant.created_at }}</td>
                <td>{{ restaurant.updated_at }}</td>
                <td>
                    <ul v-for="category in restaurant.categories">
                        <li>{{ category.name }}</li>
                    </ul>
                </td>
            </tr>
        </table>
    </div>
</template>

<script>
export default {
    name: 'GetRestaurants',
    data() {
        return {
            restaurants: this.getRestaurants()
        }
    },
    methods: {
        getRestaurants: function () {
            const axios = require('../../node_modules/axios')
            axios.get('http://localhost:1337/restaurants')
                .then(function (response) {
                    this.restaurants = response.data;
                }.bind(this))
                .catch(function (error) {
                    console.error(error)
                }.bind(this))
        }
    }
}
</script>
