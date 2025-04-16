<template>
    <div class="form">
        <div class="form__container">
            <form class="form__items" action="/submit" method="POST" id="items" @submit.prevent="submit">

                <div class="form__item" v-for="item in items" :key="item.id">
                    <label :for="item.name" class="form__label">{{ item.title }}:</label>
                    <input v-if="item.type !== 'textarea'" :type="item.type" :id="item.id" :name="item.name"
                        v-model="formData[item.name]" class="form__input" :placeholder="item.placeholder">
                    <textarea v-else :type="item.type" :id="item.id" :name="item.name" v-model="formData[item.name]"
                        class="form__input" :placeholder="item.placeholder"></textarea>
                    <p v-if="item.itemError" class="form__error-message">Заполните поле {{ item.title }}!</p>
                </div>

                <button type="submit" class="form__button">Отправить</button>

            </form>

        </div>
    </div>
</template>

<style scoped lang="scss">
@use "./../styles/mixins.scss";

.form {

    &__container {
        @include mixins.container;
        justify-content: center;

        .form__items {
            @include mixins.flex;
            flex-direction: column;
            align-items: flex-start;
            gap: 30px;

            .form__item {
                @include mixins.flex;
                flex-direction: column;
                align-items: flex-start;
                width: 360px;

                .form__label {
                    display: block;
                    font-size: 14px;
                    font-weight: bold;
                    margin-bottom: 5px;
                    color: #575757;
                }

                & input {
                    @include mixins.input;
                }

                & textarea {
                    @include mixins.textarea;
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
            items: [
                {
                    id: 'name',
                    type: 'text',
                    name: 'name',
                    title: 'Имя',
                    placeholder: 'Введите ваше Имя',
                    itemError: false
                },

                {
                    id: 'email',
                    type: 'text',
                    name: 'email',
                    title: 'Email',
                    placeholder: 'Введите ваш Email',
                    itemError: false
                },

                {
                    id: 'message',
                    type: 'textarea',
                    name: 'message',
                    title: 'Сообщение',
                    placeholder: 'Введите ваше сообщение',
                    itemError: false
                }
            ],

            formData: {},

        };
    },

    created() {
        
        this.items.forEach((item) => {
            this.formData[item.name] = '';
        });
    },

    methods: {

        validateForm() {

            this.items.forEach((item) => {
                item.itemError = false;

                if (!this.formData[item.name].trim()) {
                    return item.itemError = true;
                }
            });

        },

        submit() {
            this.validateForm();

            const result = this.items.every((item) => {
                return !item.itemError;
            });

            if (result) {
                console.log(this.formData);
            }
        }
    }
};
</script>