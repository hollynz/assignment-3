<template>
    <div class="activity-info-container">
        <div>Close</div>
    </div>
</template>

<script>
export default {
    name: "ActivityInfoContainer",
}
</script>

<style scoped>
    .activity-info-container {
        background: #c7800e;
        position: absolute;
        z-index: 1000;
        right: 0;
        bottom: 0;
        top: 0;
        margin: auto 0;
        width: 25%;
        height: 70%;
        border-top-left-radius: 20px;
        border-bottom-left-radius: 20px;
        border: solid #fff 10px;
        border-right: none;
    }
</style>


