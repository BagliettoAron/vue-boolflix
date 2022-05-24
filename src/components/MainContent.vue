<template>
<div class="main-section">
    <CardItem 
    v-for='item in movies' 
    :key='item.id' 
    :thisMovie='item'
    />
</div>
  
</template>

<script>
import CardItem from './CardItem.vue'


export default {
    name: 'MainContent',
    components: {
        CardItem
    },
    props: {
        movies: Array
    }

}
</script>

<style lang="scss" scoped>
.main-section{
    display: flex;
    flex-wrap: wrap;
    
}

</style>   