<template>
    <header class="header">
        <div class="header__container">

            <a href="/" class="header__logo">MyLogo</a>

            <nav class="header__nav">
                <ul class="header__nav-list" v-for="item in navItems">
                    <li class="header__nav-item">
                        <a :href="item.href" class="header__nav-link">{{ item.title }}</a>
                    </li>
                </ul>
            </nav>

            <div class="header__actions">
                <button class="header__btn">Войти</button>
            </div>
        </div>
    </header>
</template>

<style scoped lang="scss">
@use "./../styles/mixins.scss";

.header {
    & .header__container {
        @include mixins.container;
        padding-top: 30px;

        & .header__nav {
            @include mixins.flex;
            gap: 20px;
        }
    }
}
</style>

<script>
export default {
    data() {
        return {
            navItems: [
                {
                    href: '#home',
                    title: 'Главная'
                },

                {
                    href: '#about',
                    title: 'О нас'
                },

                {
                    href: '#services',
                    title: 'Услуги'
                },

                {
                    href: '#contact',
                    title: 'Контакты'
                },
            ]
        }
    }
}
</script>
