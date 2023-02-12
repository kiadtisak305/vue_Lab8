<script setup>
import { onMounted, ref } from 'vue';
import axios from "axios";

const show = ref(false);
const recipesData = ref([]);
const url = ref("https://www.thecocktaildb.com/api/json/v1/1/search.php?s=margarita");

function loadRecipes() {
    axios
        .get(url.value)
        .then((response) => {
            recipesData.value = response.data;
        })
        .catch((err) => {
            console.log(err);
        });
}
onMounted(loadRecipes);
</script>

<template>
    <div class="main">
        <v-card class="mx-auto" max-width="1000" v-for=" recipes in recipesData.drinks">
            <div style="display: flex;">
                <div class="image">
                    <v-img :src="recipes.strDrinkThumb" height="400px" cover></v-img>
                </div>
                <div class="text">
                    <div>
                        <v-card-title>
                            <div class="title">
                                <h3>
                                    {{ recipes.strDrink }}
                                </h3>
                            </div>
                            <div class="subtitle">
                                <p>
                                    <b>Tags : </b> <span>{{ recipes.strTags }}</span>
                                </p>
                                <p>
                                    <b>Category : </b> <span>{{ recipes.strCategory }}</span>
                                </p>
                                <p>
                                    <b>IBA : </b> <span>{{ recipes.strIBA }}</span>
                                </p>
                                <p>
                                    <b>Glass : </b> <span>{{ recipes.strGlass }}</span>
                                </p>
                            </div>
                        </v-card-title>
                        <div class="instructions">
                            <p class="text-left">
                                <b>Instructions : </b> <span>{{ recipes.strInstructions }}</span>
                            </p>
                        </div>
                        <v-card-actions>
                            <v-spacer></v-spacer>
                            <v-btn :icon="show ? 'mdi-chevron-up' : 'mdi-chevron-down'" @click="show = !show"></v-btn>
                        </v-card-actions>
                        <v-expand-transition>
                            <div v-show="show">
                                <v-divider></v-divider>
                                <v-card-text>
                                    <v-table>
                                        <thead>
                                            <tr>
                                                <th>
                                                    Ingredient
                                                </th>
                                                <th>
                                                    Measure
                                                </th>
                                            </tr>
                                        </thead>
                                        <tbody>
                                            <tr>
                                                <td>
                                                    {{ recipes.strIngredient1 }}
                                                    <br>
                                                    {{ recipes.strIngredient2 }}
                                                    <br>
                                                    {{ recipes.strIngredient3 }}
                                                    <br>
                                                    {{ recipes.strIngredient4 }}
                                                    <br>
                                                    {{ recipes.strIngredient5 }}
                                                    <br>
                                                    {{ recipes.strIngredient6 }}
                                                    <br>
                                                    {{ recipes.strIngredient7 }}
                                                </td>
                                                <td>
                                                    {{ recipes.strMeasure1 }}
                                                    <br>
                                                    {{ recipes.strMeasure2 }}
                                                    <br>
                                                    {{ recipes.strMeasure3 }}
                                                    <br>
                                                    {{ recipes.strMeasure4 }}
                                                    <br>
                                                    {{ recipes.strMeasure5 }}
                                                    <br>
                                                    {{ recipes.strMeasure6 }}
                                                    <br>
                                                    {{ recipes.strMeasure7 }}
                                                </td>
                                            </tr>
                                        </tbody>
                                    </v-table>
                                </v-card-text>
                            </div>
                        </v-expand-transition>
                    </div>
                </div>
            </div>
        </v-card>
    </div>
</template>

<style scoped>
.main {
    padding: 20px;
    background-color: #acc055;
}

.mx-auto {
    margin-top: 20px;
    margin-bottom: 50px;
    background-color: rgb(248, 255, 221);
}

.image {
    display: flex;
    flex: 1;
}

.text {
    display: flex;
    flex: 2;
}

.instructions {
    margin-top: 15px;
    margin-left: 40px;
    margin-right: 40px;
}

.subtitle {
    margin-top: 15px;
    margin-left: 60px;
    margin-right: 60px;
}

.title {
    margin-top: 30px;
    text-align: center;
}
</style>