<template>
    <div>
      <v-container class="ma-0 pa-0" grid-list-sm>
        <v-subheader>
          All Category 
        </v-subheader>
        <v-layout wrap>
          <v-flex v-for="(category) in " :key="`category-`+category.id" xs6>
            <v-card :to="'/category/'+ category.slug">
              <v-img
                :src="'http://127.0.0.1:8000/public/storage/category_images/'+category.image"
                class="white--text"
              >
                <v-card-title 
                  class="fill-height align-end"
                  v-text="category.name"
                ></v-card-title>
              </v-img>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </div>
  </template>