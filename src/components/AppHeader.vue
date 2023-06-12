<script>
export default {
    name: 'AppHeader',
    props: [
        'message'
    ]
}
</script>

<template>
    <header class="bg-white px-3 d-flex align-items-center">
        <a href="#">
            <img src="../../public/yu-gi-oh_logo.png" alt="Logo">
        </a>
        <h1>{{ message }}</h1>
    </header>
</template>

<style lang="scss" scoped>
header a img {
    width: 70px;
}

h1 {
    display: inline-block;
    margin: 0 10px;
}
</style> 