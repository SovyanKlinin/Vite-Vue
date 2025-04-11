<template>
    <div class="form">
        <div class="form__container">
            <form class="form__items" action="/submit" method="POST" id="items">

                <div class="form__item" v-for="item in items">
                    <label for="{{ item.name }}" class="form__label">{{ item.title }}</label>
                    <input v-if="item.type !== 'textarea'" type="{{ item.type }}" id="{{ item.id }}"
                        name="{{ item.name }}" class="form__input" placeholder="{{ item.type }}" required>
                    <textarea v-else type="{{ item.type }}" id="{{ item.id }}"
                        name="{{ item.name }}" class="form__input" placeholder="{{ item.type }}" required></textarea>
                </div>

                <button type="submit" class="form__button">Отправить</button>
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
            ]
        }
    }
}
</script>