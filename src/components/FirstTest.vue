<script setup>

</script>

<template>
    <div class="wrapper">
        <div class="grid-layout">
            <div class="grid-item top blue text-element">T</div>
            <div class="grid-item top white">
                <div class="white-element text-element">E</div>
            </div>
            
            <div class="grid-item bottom white">
                <div class="white-element text-element">S</div>
            </div>
            <div class="grid-item bottom blue text-element">T</div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.wrapper {
    width: 800px;
    height: 800px;
    padding: 14px;
    background-color: #0166da;
   
}
.grid-layout {
    width: 100%;
    height: 100%;
    display: inline-grid;
    grid-template-columns: auto auto;
    background-color: black;
    .grid-item {
        display: flex;
        justify-content: center;
        align-items: center !important;
        &.top {
            margin-top: 7px;
            &.blue {
                margin-left: 7px;
                box-shadow: 0 10px 1px -5px #dddddd;
            }
            &.white {
                padding-right: 7px;
            }
        }
        &.bottom {
            margin-bottom: 7px;
            &.blue {
                margin-right: 7px;
                box-shadow: 0 -10px 1px -5px #dddddd;
            }
            &.white {
                padding-left: 7px;
            }
        }
    }
   
}
.white {
    background-color: #0166da;
    .white-element {
        display: flex !important;
        justify-content: center !important;
        align-items: center !important;
        width: 100%;
        height: 100%;
        background-color: #ffffff;
        &.text-element{
            color: #404040
        }
    }
}

.blue {
    background-color: #0166da;
    position: relative;
}

.text-element {
    font-size: 150px;
    color: #000000;
}

</style>