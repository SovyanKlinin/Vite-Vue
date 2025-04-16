<template>
    <footer class="footer">
        <div class="footer__container">
            <div class="footer__wrapper">
                <div class="footer__logo">
                    <a href="/" class="footer__logo-link">MyLogo</a>
                </div>
                <nav class="footer__nav">
                    <h4 class="footer__title">Навигация</h4>
                    <ul class="footer__nav-list" v-for="item in navItems">
                        <li class="footer__nav-item">
                            <a :href="item.href" class="footer__nav-link">{{ item.title }}</a>
                        </li>
                    </ul>
                </nav>
                <div class="footer__contacts">
                    <h4 class="footer__title">Контакты</h4>
                    <div class="footer__contacts-items">
                        <p class="footer__contact-item">
                            <span>Адрес:</span> г. Москва, ул. Примерная, д. 10
                        </p>
                        <p class="footer__contact-item">
                            <span>Email:</span> info@example.com
                        </p>
                        <p class="footer__contact-item">
                            <span>Телефон:</span> +7 (999) 123-45-67
                        </p>
                    </div>
                </div>
                <div class="footer__social">
                    <h4 class="footer__title">Соцсети</h4>
                    <div class="footer__social-links" v-for="item in socialItems">
                        <a :href="item.href" target="_blank" class="footer__social-link">{{ item.title }}</a>
                    </div>
                </div>
            </div>
            <div class="footer__copyright">
                <p>&copy; 2025 MyCompany. Все права защищены.</p>
            </div>
        </div>
    </footer>
</template>

<style scoped lang="scss">
@use "./../styles/mixins.scss";

.footer {

    &__container {
        @include mixins.container;
        flex-direction: column;
        gap: 30px;
        padding: 30px 0 30px;

        .footer__wrapper {
            @include mixins.container;
            align-items: flex-start;

            .footer__nav {
                @include mixins.flex;
                flex-direction: column;
                align-items: flex-start;
                gap: 10px;
            }

            .footer__contacts {
                @include mixins.flex;
                flex-direction: column;
                align-items: flex-start;
                gap: 10px;
            }

            .footer__social {
                @include mixins.flex;
                flex-direction: column;
                align-items: flex-start;
                gap: 10px;

                &-links {
                    @include mixins.flex;
                    flex-direction: column;
                    align-items: flex-start;
                }
            }
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
            ],

            socialItems: [
                {
                    href: 'https://vk.com',
                    title: 'VK'
                },

                {
                    href: 'https://facebook.com',
                    title: 'Facebook'
                },

                {
                    href: 'https://instagram.com',
                    title: 'Instagram'
                },
            ]
        }
    }
}
</script>