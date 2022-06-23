<script setup lang="ts">
import { ElRow, ElCol, ElLink, ElCollapseTransition } from 'element-plus'
import { ref } from 'vue';

let show = ref(false)
let mobile = ref(false)
let windowWidth = ref(0)

window.addEventListener('resize', checkScreen)

function checkScreen() {
    windowWidth.value = window.innerWidth
    mobile.value = windowWidth.value < 768 
}
</script>

<template>
    <div class="container">
        <el-row class="navbar">
            <el-col :span="4">Logo</el-col>
            <el-col :span="20">
                <el-row justify="end" v-show="!mobile">
                    <el-col :span="2"><el-link target="_blank">Home</el-link></el-col>
                    <el-col :span="2"><el-link target="_blank">About</el-link></el-col>
                    <el-col :span="2"><el-link target="_blank">Profil</el-link></el-col>
                </el-row>
                <el-row justify="end" @click="show = !show" v-show="mobile">
                    <el-col :span="2"><el-link target="_blank">Open</el-link></el-col>
                </el-row>
            </el-col>
        </el-row>
        <el-collapse-transition>
            <el-row justify="center" v-show="show && mobile">
                <el-row class="mobile-link">
                    <el-col :span="2" class="nav-link-mobile"><el-link target="_blank">Home</el-link></el-col>
                    <el-col :span="2" class="nav-link-mobile"><el-link target="_blank">About</el-link></el-col>
                    <el-col :span="2" class="nav-link-mobile"><el-link target="_blank">Profil</el-link></el-col>
                </el-row>
            </el-row>
        </el-collapse-transition>
    </div>
</template>

<style>
.container {
    max-width: 1200px;
    margin: 1rem auto;
}
.mobile-link {
    flex-direction: column;
}
.nav-link-mobile {
    padding-top: 1rem;
    padding-bottom: 1rem;
}
</style>