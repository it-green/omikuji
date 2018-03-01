<template lang='pug'>
.vue-omikuji.content
    h1.header
        p  おみくじ
        p "Omikuzi is japanese fortune-telling"

    h2 Hello World!!
    div.caption
        p This is omikuzi!! Omikuzi's english name fortune!!
        p Everyone let's play this content!!
        p I'm sure you'lL like the Japanesefortune 'Omikuzi'.

    div
        button.button.is-primary#talot(@click='talot') 占う






</template>

<script lang='ts'>
import { Vue, Component } from 'vue-property-decorator';
import VueUtil from '@/scripts/util/VueUtil';
import BuefyVue from '@/components/base/BuefyVue';

/**
 * Vue Component
 */
@Component
export default class Omikuji extends BuefyVue {
    private talot(): void {
        let msg: string = '';//letで変数msgの宣言をする

        const rand: number = Math.floor(Math.random()*5);//constで定数の宣言
        switch (rand) {
            case (0): {
                msg = '大吉' ;
                break;
            }
            case (1): {
                msg = '中吉';
                break;
            }
            case (2):{
                 msg = '小吉';
                 break;
            }
            case (3):{
                msg = '吉';
                break;
            }
            case (4):{
                msg = '凶';
                break;
            }
            case (5):{
                msg ='大凶';
                break;
            }
        }
            this.$dialog.alert(msg);
    }

}

</script>

<style lang='sass' scoped>
.vue-omikuji
    padding: 16px
    text-align: center

    .header
        height: 200px

    h2
        margin: 16px auto
        color: green


    .caption
        margin: 0 auto 16px auto
        background-color: #afeeee
        width: 500px

    p
            margin: 0 auto

    button
        margin-top: 35px
        width: 20em
        height: 3em


</style>
