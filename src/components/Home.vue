<template>
    <div class="page-layout">
        <label for="sort" class="sort-style">Sort by </label>
        <select v-model="sortby" @change="selectSortby" name="sort">
            <option>Year (Oldest)</option>
            <option>Year (Newest)</option>
            <option>Alphabet</option>
        </select>
        <div class="cards-layout">
            <Card
                v-for="item in items" 
                :key="item.id" 
                :item="item" 
                @delete-card="deleteCard(item.id)"
            />
        </div>
    </div>
</template>

<script>
import Card from './Card.vue'
import axios from 'axios'

export default {
    name: 'Home',
    data() {
        return {
            items: [],
            sortby: 'Year (Oldest)'
        }
    },
    components: {
        Card
    },
    mounted() {
        axios({
            url: 'https://api.jsonbin.io/b/5f33f98ddddf413f95c2b306',
            method: 'GET',
            headers: {
                'secret-key': '$2b$10$0ve8/zpqfEF0X1kZ0TdfW.ehq645eiEhc.OykoUZABVEdE8D3bpr2'
            }
        })
            .then(res => {
                // console.log('response', res.data);

                // Shows only cars from between the year of 2000 to 2007
                this.items = res.data.filter(item => item.year >= 2000 && item.year <= 2007 );
                
                // Sort by year (default, oldest first)
                this.items.sort((a,b) => a.year - b.year);

                // Add new key
                for (var i in this.items) {
                    this.items[i] = {...this.items[i], newkey: i};
                }
                // console.log('Filtered items', this.items);
            })
    },
    methods: {
        deleteCard: function(index) {
            this.items = this.items.filter(item => item.id != index)
        },
        selectSortby: function() {
            if (this.sortby == "Year (Oldest)") {
                this.items.sort((a,b) => a.year - b.year);
            } else if(this.sortby == "Year (Newest)") {
                this.items.sort((a,b) => b.year - a.year);
            } 
            else if (this.sortby == "Alphabet") {
                // Sort by alphabet
                this.items.sort(function(a,b) {
                    var brandA = a.brand.toUpperCase();
                    var brandB = b.brand.toUpperCase();
                    if (brandA < brandB) {
                        return -1;
                    }
                    if (brandA > brandB) {
                        return 1;
                    }
                    return 0;
                });
            }

            // replace new key
            for (var i in this.items) {
                this.items[i].newkey = i;
            }
            // console.log('Filtered items', this.items);
        }
    }
}
</script>

<style scoped>
    
</style>