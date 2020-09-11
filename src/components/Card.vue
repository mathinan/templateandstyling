<template>
    <div class="card-style">
        <div class="relative">
            <p class="title-style">{{item.brand}} {{item.model}}</p>
            <button type="button" @click="$emit('delete-card')">
                <i class="fa fa-times close-icon-style"></i>
            </button>
            <p class="secondary-style">{{item.year}}</p>
            <p class="secondary-style color-style">{{item.color}}</p>
            <div class="image-style">
                <p>{{item.brand}} Image</p>
            </div>
            <p class="owner-style">Owner: {{item.owner}}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Card',
    data() {
        return {
            coloredText: null
        }
    },
    props: ['item'],
    mounted() {
        this.coloredText = document.getElementsByClassName('color-style')[this.item.newkey];
        this.coloredText.style.color = this.item.color;
    }
}
</script>

<style scoped>

</style>