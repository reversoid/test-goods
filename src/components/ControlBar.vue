<template>
    <form action="" class="form" @submit.prevent="validateAndCreateProduct()">
        <div class="form-section">
            <label class="form-section__label" for="good-name">Наименование товара</label>
            <input v-model="title" class="form-section__input" id="good-name" type="text"
                placeholder="Введите наименование товара">
            <span v-if="errors.title" class="alert">Поле является обязательным</span>
        </div>

        <div class="form-section">
            <label class="form-section__label" for="good-desc">Описание товара</label>
            <textarea v-model="description" class="form-section__input" id="good-desc" type="text"
                placeholder="Введите описание товара"></textarea>
            <span v-if="errors.description" class="alert">Поле является обязательным</span>
        </div>

        <div class="form-section">
            <label class="form-section__label" for="good-photo">Ссылка на изображение товара</label>
            <input v-model="imgLink" class="form-section__input" id="good-photo" type="text"
                placeholder="Введите ссылку">
            <span v-if="errors.imgLink" class="alert">Поле является обязательным</span>
        </div>

        <div class="form-section mb15">
            <label class="form-section__label" for="good-price">Цена товара</label>
            <input v-model="price" class="form-section__input" id="good-price" type="text" placeholder="Введите цену">
            <span v-if="errors.price" class="alert">Поле является обязательным</span>
        </div>
        <button :disabled="title === '' || description === '' || price === '' || imgLink === ''" type="submit" class="form__submit">Добавить товар</button>
    </form>
</template>

<script>
export default {
    name: 'ControlBar',
    props: {
        _createProduct: Function,
    },
    data() {
        return {
            title: '',
            description: '',
            imgLink: '',
            price: '',
            errors: {
                title: false,
                description: false,
                imgLink: false,
                price: false,
            }
        }
    },
    methods: {
        _resetForm() {
            this.title = '';
            this.description = '';
            this.imgLink = '';
            this.price = '';
        },
        _findErrors() {
            this.errors.description = this.description === '';
            this.errors.title = this.title === '';
            this.errors.imgLink = this.imgLink === '';
            this.errors.price = this.price === '';
        },
        _errorExist() {
            for (let property in this.errors) {
                if (this.errors[property]) return true;
            }
            return false;
        },
        validateAndCreateProduct() {
            this._findErrors();
            if (this._errorExist()) return;
            
            this._createProduct(this.imgLink, this.title, this.description, this.price);
            this._resetForm();
        }
    }
}
</script>

<style lang="scss">
.form {
    height: fit-content;
    border-radius: 0.25rem;
    width: 20.75rem;
    padding: 1.5rem;
    background-color: #FFFEFB;

    .form__submit {
        &:disabled {
            background-color: #EEEEEE;
            color: #B4B4B4;
        }

        font-size: 0.75rem;
        border-radius: 0.625rem;
        padding: 0.625rem 1rem;
        background-color: #7BAE73;
        width: 100%;
        text-align: center;
        color: #fff;
        font-weight: 600;
    }

    .form-section {
        position: relative;
        margin-bottom: 1rem;
        display: flex;
        flex-direction: column;

        &.mb15 {
            margin-bottom: 1.5rem;
        }

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

            &:focus {
                box-shadow: 0 0 0.25rem rgb(122, 122, 122);
            }
        }

        .alert {
            position: absolute;
            font-size: 0.5rem;
            color: #FF8484;
            bottom: -0.7rem;
            left: 0;
        }
    }
}
</style>