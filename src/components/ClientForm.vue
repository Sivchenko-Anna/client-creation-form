<template>
  <div>
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
            placeholder="Котейкин"
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
            placeholder="Иван"
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
            placeholder="Васильевич"
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
          <div
            class="error"
            v-if="$v.birthdate.$dirty && !$v.birthdate.required"
          >
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
          <label for="sendSms" class="client-form__label"
            >Не отправлять СМС:</label
          >
          <div class="client-form__option">
            <input
              id="sendSms"
              type="checkbox"
              class="client-form__checkbox"
              true-value="Не отправлять СМС"
              false-value="Отправить СМС"
            />
            <span class="client-form__option-text">Да</span>
          </div>
        </div>
      </fieldset>

      <fieldset class="client-form__fieldset">
        <div class="client-form__group">
          <label for="index" class="client-form__label">Индекс</label>
          <input
            id="index"
            type="text"
            v-model="index"
            class="client-form__input"
            placeholder="455001"
          />
        </div>
        <div class="client-form__group">
          <label for="country" class="client-form__label">Страна</label>
          <input
            id="country"
            type="text"
            v-model="country"
            class="client-form__input"
            placeholder="Россия"
          />
        </div>
        <div class="client-form__group">
          <label for="region" class="client-form__label">Область</label>
          <input
            id="region"
            type="text"
            v-model="region"
            class="client-form__input"
            placeholder="Челябинская"
          />
        </div>
        <div class="client-form__group">
          <label for="city" class="client-form__label required">Город</label>
          <input
            id="city"
            type="text"
            v-model="city"
            class="client-form__input"
            placeholder="Челябинск"
          />
          <div class="error" v-if="$v.city.$dirty && !$v.city.required">
            Обязательное поле
          </div>
        </div>
        <div class="client-form__group">
          <label for="street" class="client-form__label">Улица</label>
          <input
            id="street"
            type="text"
            v-model="street"
            class="client-form__input"
            placeholder="Герцена"
          />
        </div>
        <div class="client-form__group">
          <label for="house" class="client-form__label">Дом</label>
          <input
            id="house"
            type="text"
            v-model="house"
            class="client-form__input"
            placeholder="6"
          />
        </div>
      </fieldset>

      <fieldset class="client-form__fieldset">
        <div class="client-form__group">
          <label for="document" class="client-form__label required"
            >Тип документа:</label
          >
          <select id="document" v-model="document" class="client-form__select">
            <option value="">Выберите тип документа</option>
            <option value="Паспорт">Паспорт</option>
            <option value="Свидетельство о рождении">
              Свидетельство о рождении
            </option>
            <option value="Вод. удостоверение">Вод. удостоверение</option>
          </select>
          <div class="error" v-if="$v.document.$dirty && !$v.document.required">
            Обязательное поле
          </div>
        </div>
        <div class="client-form__group">
          <label for="series" class="client-form__label">Серия</label>
          <input
            id="series"
            type="text"
            v-model="series"
            class="client-form__input"
            placeholder="1234"
          />
        </div>
        <div class="client-form__group">
          <label for="number" class="client-form__label">Номер</label>
          <input
            id="number"
            type="text"
            v-model="number"
            class="client-form__input"
            placeholder="567890"
          />
        </div>
        <div class="client-form__group">
          <label for="issued-by" class="client-form__label">Кем выдан</label>
          <input
            id="issued-by"
            type="text"
            v-model="issuedBy"
            class="client-form__input"
            placeholder="УМВД России"
          />
        </div>
        <div class="client-form__group">
          <label for="issuedate" class="client-form__label required"
            >Дата выдачи
          </label>
          <input
            id="issuedate"
            type="date"
            v-model="$v.issuedate.$model"
            class="client-form__input"
          />
          <div
            class="error"
            v-if="$v.issuedate.$dirty && !$v.issuedate.required"
          >
            Обязательное поле
          </div>
        </div>
      </fieldset>

      <button class="client-form__submit-button" type="submit">
        Отправить
      </button>
    </form>
    <div v-if="isClientCreated" class="modal">
    <div class="modal__content">
      <span class="modal__success-message">Новый клиент успешно создан!</span>
    </div>
  </div>
  </div>
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
    index: "",
    country: "",
    region: "",
    city: "",
    street: "",
    house: "",
    document: "",
    series: "",
    number: "",
    issuedBy: "",
    issuedate: "",
    isClientCreated: true,
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
    city: {
      required,
    },
    document: {
      required,
    },
    issuedate: {
      required,
    },
  },
  computed: {
    isFormValid() {
      const requiredFields = [
        "surname",
        "name",
        "birthdate",
        "phone",
        "clientGroup",
        "city",
        "document",
        "issuedate",
      ];

      const isEmpty = requiredFields.some((field) => !this[field]);
      const hasErrors = requiredFields.some((field) => this.$v[field].$error);

      return !isEmpty && !hasErrors;
    },
  },
  methods: {
    submitForm() {
      if (!this.isFormValid) {
        console.log("Пожалуйста, заполните все обязательные поля");
        return;
      }

      this.isClientCreated = true;
      setTimeout(() => {
        this.isClientCreated = false;
      }, 3000);
    },
  },
};
</script>
