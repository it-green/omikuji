<template lang='pug'>
.vue-index
    .reactive-title {{ reactiveTitle() }}
    omikuji
</template>

<script lang='ts'>
import { Vue, Component } from 'vue-property-decorator';
import VueUtil from '@/scripts/util/VueUtil';
import RootVue from '@/components/base/RootVue';
import Omikuji from '@/components/part/Omikuji.vue';

import 'mdi/scss/materialdesignicons.scss';
import Buefy from 'buefy';
import 'buefy/lib/buefy.min.css';

Vue.use(Buefy);

/**
 * Vue Component
 */
@Component
export default class Index extends RootVue {
    public title: string = 'おみくじ';

    protected beforeCreate(): void {
        // Inner Vue 登録
        VueUtil.registerComponents([Omikuji]);
    }
}
</script>

<style lang='sass'>
@import '../../styles/color.sass'
@import '../../styles/common.sass'

@import '~bulma/sass/utilities/_all'


$primary: skyblue
$colors: ('white': ($white, $black), 'black': ($black, $white), 'light': ($light, $light-invert), 'dark': ($dark, $dark-invert), 'primary': ($primary, $primary-invert), 'info': ($info, $info-invert), 'success': ($success, $success-invert), 'warning': ($warning, $warning-invert), 'danger': ($danger, $danger-invert))

.vue-index

@import '~bulma'
@import '~buefy/src/scss/buefy'
</style>
