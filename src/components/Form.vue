<template>
    <div class="form">
        <div class="form__container">
            <form class="form__items" action="/submit" method="POST" id="items" @submit.prevent="Submit">

                <div class="form__item" v-for="item in items" :key="item.id">
                    <label :for="item.name" class="form__label">{{ item.title }}</label>
                    <input v-if="item.type !== 'textarea'" :type="item.type" :id="item.id" :name="item.name"
                        v-model="formData[item.name]" class="form__input" :placeholder="item.placeholder">
                    <textarea v-else :type="item.type" :id="item.id" :name="item.name" v-model="formData[item.name]"
                        class="form__input" :placeholder="item.placeholder"></textarea>
                </div>

                <button type="submit" class="form__button">Отправить</button>

                <p v-show="formError" class="form__error-message">Не все поля заполнены!</p>
            </form>

        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            items: [
                {
                    id: 'name',
                    type: 'text',
                    name: 'name',
                    title: 'Имя:',
                    placeholder: 'Введите ваше Имя'
                },

                {
                    id: 'email',
                    type: 'text',
                    name: 'email',
                    title: 'Email:',
                    placeholder: 'Введите ваше Email'
                },

                {
                    id: 'message',
                    type: 'textarea',
                    name: 'message',
                    title: 'Сообщение:',
                    placeholder: 'Введите ваше сообщение'
                }
            ],

            formData: {},

            formError: false,

        };
    },

    created(items) {
        items = this.items;

        items.forEach((item) => {
            this.formData[item.name] = '';
        });
    },

    methods: {

        validateForm() {
            this.formError = false;

            for (const key in this.formData) {
                if (!this.formData[key].trim()) {
                    return this.formError = true;
                }
            }

            return !this.formError;
        },

        Submit() {
            this.validateForm();
            console.log(this.formData);
        }
    }
};
</script>