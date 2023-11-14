<template>
  <form class="client-form" @submit.prevent="submitForm">
    <fieldset class="client-form__fieldset">
      <div class="client-form__group">
        <label for="surname" class="client-form__label required"
          >Фамилия
        </label>
        <input
          id="surname"
          type="text"
          v-model.trim="$v.surname.$model"
          class="client-form__input"
        />
        <div class="error" v-if="$v.surname.$dirty && !$v.surname.required">
          Обязательное поле
        </div>
      </div>
      <div class="client-form__group">
        <label for="name" class="client-form__label required">Имя </label>
        <input
          id="name"
          type="text"
          v-model.trim="$v.name.$model"
          class="client-form__input"
        />
        <div class="error" v-if="$v.name.$dirty && !$v.name.required">
          Обязательное поле
        </div>
        <div class="error" v-if="!$v.name.minLength">
          Имя должно содержать не менее
          {{ $v.name.$params.minLength.min }} символов
        </div>
      </div>
      <div class="client-form__group">
        <label for="patronymic" class="client-form__label">Отчество</label>
        <input
          id="patronymic"
          type="text"
          v-model="patronymic"
          class="client-form__input"
        />
      </div>
      <div class="client-form__group">
        <label for="birthdate" class="client-form__label required"
          >Дата рождения
        </label>
        <input
          id="birthdate"
          type="date"
          v-model="$v.birthdate.$model"
          class="client-form__input"
        />
        <div class="error" v-if="$v.birthdate.$dirty && !$v.birthdate.required">
          Обязательное поле
        </div>
      </div>
      <div class="client-form__group">
        <label for="phone" class="client-form__label required"
          >Номер телефона
        </label>
        <input
          id="phone"
          type="tel"
          v-model="$v.phone.$model"
          pattern="^7[0-9]{10}$"
          class="client-form__input"
          placeholder="+7 (123) 456-78-90"
        />
        <div class="error" v-if="$v.phone.$dirty && !$v.phone.required">
          Обязательное поле
        </div>
        <div class="error" v-if="!$v.phone.minLength">
          Телефон должен содержать
          {{ $v.phone.$params.minLength.min }} цифр и начинаться с 7
        </div>
      </div>
      <div class="client-form__group">
        <label for="gender" class="client-form__label">Пол</label>
        <select id="gender" v-model="gender" class="client-form__select">
          <option value="">Выберите пол</option>
          <option value="Мужской">Мужской</option>
          <option value="Женский">Женский</option>
        </select>
      </div>
      <div class="client-form__group">
        <label for="clientGroup" class="client-form__label required"
          >Группа клиентов:
        </label>
        <select
          id="clientGroup"
          v-model="$v.clientGroup.$model"
          multiple
          class="client-form__select"
          size="1"
        >
          <option value="VIP">VIP</option>
          <option value="Проблемные">Проблемные</option>
          <option value="ОМС">ОМС</option>
        </select>
        <div
          class="error"
          v-if="$v.clientGroup.$dirty && !$v.clientGroup.required"
        >
          Обязательное поле
        </div>
      </div>
      <div class="client-form__group">
        <label for="doctor" class="client-form__label">Лечащий врач:</label>
        <select id="doctor" v-model="doctor" class="client-form__select">
          <option value="">Выберите врача</option>
          <option value="Иванов">Иванов</option>
          <option value="Захаров">Захаров</option>
          <option value="Чернышева">Чернышева</option>
        </select>
      </div>
      <div class="client-form__group">
        <label for="sendSms" class="client-form__label">Отправлять СМС:</label>
        <div class="client-form__option">
          <input id="sendSms" type="checkbox" class="client-form__checkbox" />
          <span class="client-form__option-text">Да</span>
        </div>
        <div class="client-form__option">
          <input id="noSms" type="checkbox" class="client-form__checkbox" />
          <span class="client-form__option-text">Нет</span>
        </div>
      </div>
    </fieldset>

    <button class="client-form__submit-button" type="submit">Отправить</button>
  </form>
</template>

<script>
import { required, minLength } from "vuelidate/lib/validators";

export default {
  name: "ClientForm",
  data: () => ({
    surname: "",
    name: "",
    patronymic: "",
    birthdate: "",
    phone: "",
    gender: "",
    clientGroup: [],
    doctor: "",
    noSms: false,
  }),
  validations: {
    surname: {
      required,
    },
    name: {
      required,
      minLength: minLength(2),
    },
    birthdate: {
      required,
    },
    phone: {
      required,
      minLength: minLength(11),
    },
    clientGroup: {
      required,
    },
  },
  methods: {
    submitForm() {
      const requiredFields = [
        "surname",
        "name",
        "birthdate",
        "phone",
        "clientGroup",
      ];

      const isEmpty = requiredFields.some(field => !this[field]);
      const errors = requiredFields.filter((field) => this.$v[field].$error);

      if (errors.length > 0 || isEmpty) {
        console.log("Пожалуйста, заполните все обязательные поля");
        return;
      }
      console.log("Данные формы:", this.surname, this.name, this.birthdate);
    },
  },
};
</script>
