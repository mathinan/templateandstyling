<template>
    <div>
        <p class="color-title">{{group[0].color}}</p>
        <div class="cards-layout">
            <ColorCard 
                v-for="item in group"
                :key="item.id" 
                :item="item"
            />
        </div>
    </div>
</template>

<script>
import ColorCard from './ColorCard'

export default {
    name: 'Color',
    components: {
        ColorCard
    },
    props: ['group']
}
</script>

<style scoped>

</style>