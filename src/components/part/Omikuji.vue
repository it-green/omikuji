<template lang='pug'>
.vue-omikuji.content
    header.hero.is-success
        .hero-body: .container
            h1.title おみくじ
            h2.subtitle "Omikuzi is japanese fortune-telling"

    section.main: .container
        h2  みなさんこんにちは!!
        h2  Hello World!!
        div.caption
            p これはおみくじです。
            p 下の方にある、占いボタンを押してくだい。
            p 今日の運勢を占うことができます。

            p ※This is omikuzi!! Omikuzi's english name fortune!!
            p Everyone let's play this content!!
            p I'm sure you'lL like the Japanesefortune 'Omikuzi'.

        button.button.is-medium.is-primary.buefyicon(@click='talot') 占う

        b-modal(:active.sync='activeModal' width='700' scroll='keep')
            .telling.card
                h3.title {{ fortune }}
                p {{ message }}

        div.snackbar
            button.button.is-medium.is-warning(@click='warning') ひとこと

    footer.footer
        div.container
            div.content.has-text-centered
                p
                    strong omikuji by RyotaroKato

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
    private activeModal: boolean = false;
    private fortune: string = '';
    private message: string = '';


    private talot(): void {
        const rand: number = Math.floor(Math.random()*5);//constで定数の宣言
        switch (rand) {
            case (0): {
                this.fortune = '大吉' ;
                this.message = '今日のあなたの運勢は大吉です!!いいことがありそうな予感がします!!良い一日を遅れること間違いなしです。';
                break;
            }
            case (1): {
                this.fortune = '中吉';
                this.message = 'あなたの運勢は、中吉です。なかなかいい感じですね!!健康で安全な生活ができそうです。';
                break;
            }
            case (2):{
                this.fortune = '小吉';
                this.message = '小吉です!!ほんのちょっとの心がけで、もっといいことが起こるかもしれません。頑張って、運を自分の元へと引き寄せましょう!!';
                break;
            }
            case (3):{
                this.fortune = '吉';
                this.message = '今日は、可もなく不可もなくな1日です。特に悪いことも起こりませんが、そんな幸運に惠まれることはなさそうです。';
                break;
            }
            case (4):{
                this.fortune = '凶';
                this.message = 'ちょっとよくないですね。今日は、無理をしすぎないで、できるだけ面倒ごとを避けましょう。触らぬ神に祟なしです。';
                break;
            }
            case (5):{
                this.fortune ='大凶';
                this.message = 'ごめんなさい!!｀大凶です’いつもより気をつけて生活をしてみましょう。あまり気を落とさずに、いつも通りの生活を心がけてみましょう。';
                break;
            }
        }

        this.activeModal = true;
    }

    private warning(): void {
        this.$snackbar.open('おみくじっていいですね');
    }


}

</script>

<style lang='sass' scoped>
.vue-omikuji
    .title
        font-family: suns-serif

    section.main
        padding: 16px
        text-align: center

        h2
            margin: 10px auto
            color: green

        .caption
            margin: 0 auto 16px auto
            background-color: #afeeee
            max-width: 500px

        p
            margin: 0 auto

        button
            margin-top: 35px
            width: 10em
            height: 2.5em

        .telling
            padding: 16px
            background-color: #98FB98
            height: 150px
            p
                padding: 10px
        .footer
            margin-top: 140px
</style>
