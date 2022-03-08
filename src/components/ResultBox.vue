<template>
    <p>You catch me on {{Score}} ms.</p>
    <div v-if="Score < 300">
        <p>You are amazing man ^_^</p>
    </div>

    <div v-else-if="Score > 300 && Score > 600">
        <p>You are normal (•_•)</p>
    </div>

    <div v-else>
        <p >You are too slow ಠ_ಠ</p>
    </div>
</template>

<script>
export default {
    props:['Score']
}
</script>

<style>
.ResultBox p{
    font-size: 18px;
}
</style>