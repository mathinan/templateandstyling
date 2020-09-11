<template>
    <div class="page-layout">
        <Color 
            v-for="(group, index) in groupedByColor"
            :key="index" 
            :group="group"
        />
    </div>
</template>

<script>
import axios from 'axios'
import _ from 'lodash'
import Color from './Color'

export default {
    name: 'ViewByColor',
    data() {
        return {
            items: [],
            groupedByColor: []
        }
    },
    components: {
        Color
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
                // console.log('Filtered items', this.items);

                // Sort by color
                this.groupedByColor = _.groupBy(this.items, 'color');
                // console.log('Grouped by color', this.groupedByColor);
            })
    }
}
</script>

<style scoped>

</style>