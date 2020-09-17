<template>
    <section class="section">
        <div>
            <h1 :style="{ 'backgroundColor': selectedVtuber.color }">{{ selectedVtuber.name }}</h1>
            <img :src="selectedVtuber.image" alt="">
        </div>
    </section>
</template>

<script>
export default {
    mounted() {
        this.selectedVtuber = this.getVtuberById(this.$route.params.id)
    },
    data() {
        return {
            vtubers: [
                { id: 1, name: '月ノ美兎', twitter: '@Tsukinomito', image: 'https://nijisanji.ichikara.co.jp/wp-content/uploads/elementor/thumbs/%E6%9C%88%E3%83%8E%E7%BE%8E%E5%85%8E%E9%80%9A%E5%B8%B8_1-e1549528387192-o35s233kw988aand6zwc8avw4x228z5dhh21eaxe6c.png', color: "#696969" },
                { id: 2, name: '本間ひまわり', twitter: '@honmahimawari', image: 'https://nijisanji.ichikara.co.jp/wp-content/uploads/elementor/thumbs/-e1546940827410-o2bvtk62wmw63h8g0gnomcjoxnw64g2f9viu79tjp6.png', color: "#f1f1f1" },
                { id: 3, name: '百鬼あやめ', twitter: '@nakiriayame', image: 'https://user-images.strikinglycdn.com/res/hrscywv4p/image/upload/c_limit,fl_lossy,h_1000,w_500,f_auto,q_auto/1369026/808112_469591.png'
                , zokusei: ['HoloLive', 'かわ余'], color: '#565656' },
            ],
            selectedVtuber: {},
        }
    },

    methods: {
        getVtuberById:function(id) {
            let vtuber = this.vtubers[2]
            for (let i = 0; this.vtubers.length > i; i++) {
                if (this.vtubers[i].id == id) {
                    vtuber = this.vtubers[i]
                }
            }
            console.log(this.selectedVtuber)
            return vtuber
        }
    },
}
</script>