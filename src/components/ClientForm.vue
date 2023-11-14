<template>
  <form class="client-form" @submit.prevent="submitForm">
    <fieldset class="client-form__fieldset">
      <div class="client-form__group">
        <label for="surname" class="client-form__label required">Фамилия </label>
        <input
          id="surname"
          type="text"
          v-model="surname"
          required
          class="client-form__input"
        />
      </div>
      <div class="client-form__group">
        <label for="name" class="client-form__label required">Имя </label>
        <input
          id="name"
          type="text"
          v-model="name"
          required
          class="client-form__input"
        />
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
        <label for="birthdate" class="client-form__label required">Дата рождения </label>
        <input
          id="birthdate"
          type="date"
          v-model="birthdate"
          required
          class="client-form__input"
        />
      </div>
      <div class="client-form__group">
        <label for="phone" class="client-form__label required">Номер телефона </label>
        <input
          id="phone"
          type="tel"
          v-model="phone"
          pattern="[7]{1}[0-9]{10}"
          required
          class="client-form__input"
        />
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
          >Группа клиентов: </label
        >
        <select
          id="clientGroup"
          v-model="clientGroup"
          multiple
          class="client-form__select"
          size="1"
        >
          <option value="VIP">VIP</option>
          <option value="Проблемные">Проблемные</option>
          <option value="ОМС">ОМС</option>
        </select>
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
          <input
            id="sendSms"
            type="checkbox"
            v-model="sendSms"
            class="client-form__checkbox"
          />
          <span class="client-form__option-text">Да</span>
        </div>
        <div class="client-form__option">
          <input
            id="noSms"
            type="checkbox"
            v-model="noSms"
            class="client-form__checkbox"
          />
          <span class="client-form__option-text">Нет</span>
        </div>
      </div>
    </fieldset>

    <button class="client-form__submit-button" type="submit">Отправить</button>
  </form>
</template>

<script>
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
  methods: {
    submitForm() {
      console.log("Данные формы:", this.name, this.email, this.message);
    },
  },
};
</script>
