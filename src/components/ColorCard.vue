<template>
    <div class="card-style">
        <div class="relative">
            <p class="title-style">{{item.brand}}</p>
            <p class="secondary-style" style="color: #707070;">Model: {{item.model}}</p>
            <p class="secondary-style">Year: {{item.year}}</p>
            <div class="image-style">
                <p>{{item.brand}} Image</p>
            </div>
            <p class="owner-style">Owner: {{item.owner}}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ColorCard',
    props: ['item']
}
</script>

<style scoped>

</style>