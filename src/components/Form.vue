<template>
    <div class="form">
        <div class="form__container">
            <form class="form__items" action="/submit" method="POST">
                <div class="form__item">
                    <label for="name" class="form__label">Имя:</label>
                    <input type="text" id="name" name="name" class="form__input" placeholder="Введите ваше имя"
                        required />
                </div>

                <div class="form__item">
                    <label for="email" class="form__label">Email:</label>
                    <input type="email" id="email" name="email" class="form__input" placeholder="Введите ваш email"
                        required />
                </div>

                <div class="form__item">
                    <label for="message" class="form__label">Сообщение:</label>
                    <textarea id="message" name="message" class="form__textarea" placeholder="Введите ваше сообщение"
                        rows="4" required></textarea>
                </div>

                <button type="submit" class="form__button">Отправить</button>
            </form>
        </div>
    </div>
</template>