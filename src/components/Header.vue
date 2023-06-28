<script>
export default {
    data() {
        return {
            isNavVisible: false
        }
    }
}
</script>

<template>
    <header class="header">
        <div class="overlay" :class="{show: isNavVisible}"></div>
        <button @click="isNavVisible = !isNavVisible" :class="{active: isNavVisible}" class="header__btn"></button>
        <a href="/">
            <img src="../assets/images/logo.svg" alt="Room Logo" class="header__brand">
        </a>
        <nav class="header__nav" :class="{show: isNavVisible}">
            <a class="nav-link" href="#">home</a>
            <a class="nav-link" href="#">about</a>
            <a class="nav-link" href="#">shop</a>
            <a class="nav-link" href="#">contact</a>
        </nav>
    </header>
</template>

<style lang="scss" scoped>
@import '../main.scss';

.header {
    position: absolute;
    top: 0;
    left: 0;
    padding: 60px;
    display: flex;
    align-items: center;
    gap: 55px;
    z-index: 10;

    @media only screen and (max-width: 475px) {
        position: fixed;
        padding: 30px 0;
        justify-content: center;
        width: 100%;
    }

    .overlay {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background: rgba(0,0,0,0.5);
        z-index: 2;
        pointer-events: none;
        display: none;

        &.show {
            display: block;
        }
    }

    &__btn {
        width: 30px;
        height: 30px;
        border: none;
        background-color: transparent;
        background: center no-repeat url('../assets/images/icon-hamburger.svg');
        cursor: pointer;
        display: none;
        z-index: 12;

        &.active {
            background-image: url('../assets/images/icon-close.svg');
        }

        @media only screen and (max-width: 475px) {
            display: inline-block;
            position: fixed;
            top: 22px;
            left: 16px;
        }
    }

    &__brand {
        width: 60px;

        @media only screen and (max-width: 475px) {}
    }

    &__nav {
        display: flex;
        gap: 30px;

        &.show {
            display: flex;
        }

        @media only screen and (max-width: 475px) {
            position: fixed;
            width: 100%;
            top: 0;
            left: 0;
            padding: 30px;
            padding-left: 60px;
            justify-content: center;
            background: $white;
            display: none;
            z-index: 10;
        }

        .nav-link {
            position: relative;
            font-size: $fs-md;
            text-decoration: none;
            color: $white;

            @media only screen and (max-width: 475px) {
                color: $black;
            }

            &::before {
                content: '';
                position: absolute;
                top: 20px;
                left: 50%;
                transform: translateX(-50%);
                width: 15px;
                height: 2px;
                background: $white;
                transition: $ts-200;
                opacity: 0;
            }

            &:hover::before {
                opacity: 1;
            }
        }
    }
}
</style>
