<template>
    <main>
        <BaseFilm/>
        <BaseTv/>
    </main>
</template>

<script>

import BaseFilm from '../common/BaseFilm.vue'
import BaseTv from '../common/BaseTv.vue'

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