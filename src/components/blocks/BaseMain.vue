<template>
    <main>
        <BaseFilm/>
        <BaseTv/>
    </main>
</template>

<script>

import BaseFilm from '../sections/BaseFilm.vue'
import BaseTv from '../sections/BaseTv.vue'

export default {
    name: 'BaseMain',
    components: {
        BaseFilm,
        BaseTv,
    }
}

</script>

<style lang="scss" scoped>
</style>