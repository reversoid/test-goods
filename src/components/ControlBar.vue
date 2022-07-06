<template>
    <form action="" class="form">
        <div class="form-section">
            <label class="form-section__label" for="good-name">Наименование товара</label>
            <input class="form-section__input" id="good-name" type="text" placeholder="Введите наименование товара">
        </div>

        <div class="form-section">
            <label class="form-section__label" for="good-desc">Описание товара</label>
            <textarea class="form-section__input" id="good-desc" type="text" placeholder="Введите описание товара"></textarea>
        </div>

        <div class="form-section">
            <label class="form-section__label" for="good-photo">Ссылка на изображение товара</label>
            <input class="form-section__input" id="good-photo" type="text" placeholder="Введите ссылку">
        </div>

        <div class="form-section">
            <label class="form-section__label" for="good-price">Цена товара</label>
            <input class="form-section__input" id="good-price" type="text" placeholder="Введите цену">
        </div>
    </form>
</template>

<script>
export default {
    name: 'ControlBar',
}
</script>

<style lang="scss">
.form {
    width: 20.75rem;
    padding: 1.5rem;
    background-color: #FFFEFB;
}
    .form-section {
        margin-bottom: 1rem;
        display: flex;
        flex-direction: column;

        .form-section__label {
            font-size: 0.625rem;
            margin-bottom: 0.25rem;
        }
        textarea {
            resize: vertical;
        }
        .form-section__input {
            padding: 0.625rem 1rem;
            box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
            border-radius: 0.25rem;
            font-size: 0.75rem;
            &::placeholder {
                color: #B4B4B4;
            }
        }
    }
</style>