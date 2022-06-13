<template>
    <main class="bg-dark">
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

main {
    min-height: calc(100vh - 80px);
}
</style>