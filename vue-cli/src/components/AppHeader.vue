<!-- 컴포넌트 명칭은 두 단어로 하는게 좋음.
why? -> 다른 페이지에서 불러 올 경우 컴포넌트명 혼동 방지 -->
<template>
    <header>
        <h1>{{propsdata}}</h1>
        <button v-on:click="sendEvent">send</button>
    </header>
</template>

<script>
export default {
    props: ['propsdata'],
    methods: {
        sendEvent: function() {
            this.$emit('renew')
        }    
    }
}
</script>

<style>

</style>