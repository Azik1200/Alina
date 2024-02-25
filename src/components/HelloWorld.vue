<template>
  <div class="client-form">
    <!-- Личные данные -->
    <div class="section">
      <h2>Личные данные</h2>
      <input v-model="surname" type="text" placeholder="Фамилия">
      <!-- Остальные поля для имени, отчества, даты рождения, номера телефона, пола и группы клиентов -->
      <!-- Добавьте здесь валидацию для каждого поля -->
    </div>

    <!-- Адрес -->
    <div class="section">
      <h2>Адрес</h2>
      <input v-model="surname" type="text" placeholder="Адрес">
    </div>

    <!-- Паспорт -->
    <div class="section">
      <h2>Паспорт</h2>
      <input v-model="surname" type="text" placeholder="Паспорт">
    </div>

    <!-- Опция не отправлять СМС -->
    <div class="section">
      <input type="checkbox" v-model="noSms"> Не отправлять СМС
    </div>

    <!-- Кнопка для отправки формы -->
    <button @click="submitForm">Создать клиента</button>

    <!-- Вывод сообщения об успешном создании клиента или ошибок -->
    <div v-if="successMessage">{{ successMessage }}</div>
    <div v-if="errorMessage">{{ errorMessage }}</div>
  </div>
</template>

<script>
import { required } from 'vuelidate/lib/validators';

export default {
  data() {
    return {
      // Здесь храните данные формы
      surname: '',
      // Добавьте здесь остальные поля формы
      noSms: false,
      successMessage: '',
      errorMessage: ''
    };
  },
  validations: {
    surname: {
      required,
      // Добавьте другие правила валидации для каждого поля
    },
    // Добавьте здесь валидацию для остальных полей формы
  },
  methods: {
    submitForm() {
      // Проверка валидации перед отправкой формы
      this.$v.$touch();
      if (!this.$v.$invalid) {
        // Отправка данных формы
        // Показать сообщение об успешном создании клиента
        this.successMessage = 'Новый клиент успешно создан!';
      } else {
        // Показать сообщение об ошибке валидации
        this.errorMessage = 'Пожалуйста, заполните форму корректно.';
      }
    }
  }
};
</script>

<style lang="scss">
.client-form {
  // Стили для формы
}

.section {
  // Стили для секций формы
}
</style>
