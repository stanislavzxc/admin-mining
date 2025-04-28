<script>
export default {
  name: "SiteSettings",
  components: {},
  data() {
    return {
      top: true,
      market: true,
      help_center: true,
      support: true,
      business: true,
      stat: true,
      dash: true,
      payments: true,
      miners: true,
      accuruals: true,
      test: true,
      test_mode: true,
      tech: false,
      register: false,
    };
  },
  methods: {},
};
</script>
<template>
  <section class="wrapper">
    <div class="card">
      <h2>Управление разделами</h2>
      <div class="wrap-check">
        <input type="checkbox" v-model="top" id="top" class="checkbox" />
        <label for="top" class="group-value">ТОП 20</label>
      </div>
      <div class="wrap-check">
        <input type="checkbox" v-model="market" id="market" class="checkbox" />
        <label for="market" class="group-value">Маркетплейс</label>
      </div>
      <div class="wrap-check">
        <input
          type="checkbox"
          v-model="help_center"
          id="help_center"
          class="checkbox"
        />
        <label for="help_center" class="group-value">Справочный центр</label>
      </div>
      <div class="wrap-check">
        <input
          type="checkbox"
          v-model="support"
          id="support"
          class="checkbox"
        />
        <label for="support" class="group-value">Тех поддержка</label>
      </div>
      <div class="wrap-check">
        <input
          type="checkbox"
          v-model="business"
          id="business"
          class="checkbox"
        />
        <label for="business" class="group-value">Готовый бизнес</label>
      </div>
      <div class="wrap-check">
        <input type="checkbox" v-model="stat" id="stat" class="checkbox" />
        <label for="stat" class="group-value">Моя статистика</label>
      </div>
      <div class="wrap-check">
        <input type="checkbox" v-model="dash" id="dash" class="checkbox" />
        <label for="dash" class="group-value">Дашбоард</label>
      </div>
      <div class="wrap-check">
        <input
          type="checkbox"
          v-model="payments"
          id="payments"
          class="checkbox"
        />
        <label for="payments" class="group-value">Мои платежи</label>
      </div>
      <div class="wrap-check">
        <input type="checkbox" v-model="miners" id="miners" class="checkbox" />
        <label for="miners" class="group-value">Мои майнеры</label>
      </div>
      <div class="wrap-check">
        <input
          type="checkbox"
          v-model="accuruals"
          id="accuruals"
          class="checkbox"
        />
        <label for="accuruals" class="group-value">Начисление списание</label>
      </div>
      <div class="wrap-check">
        <input type="checkbox" v-model="test" id="test" class="checkbox" />
        <label for="test" class="group-value">Тест режим</label>
      </div>
    </div>
    <div class="card">
      <h2>Управление сайтом</h2>
      <div class="wrap-group">
        <div class="group">
          <label for="test_mode" class="group-value">Тест Режим</label>
          <select
            type="text"
            id="test_mode"
            name="test_mode"
            v-model="test_mode"
            class="group-item"
          >
            <option :value="true">Включен</option>
            <option :value="false">Выключен</option>
          </select>
        </div>
        <div class="group">
          <label for="tech" class="group-value"
            >Закрыть сайт на тех. работу</label
          >
          <select
            type="text"
            id="tech"
            name="tech"
            v-model="tech"
            class="group-item"
          >
            <option :value="true">Да</option>
            <option :value="false">Нет</option>
          </select>
        </div>
      </div>
      <div class="group">
        <label for="register" class="group-value">Закрыть регистрацию</label>
        <select
          type="text"
          id="register"
          name="register"
          v-model="register"
          class="group-item"
        >
          <option :value="true">Да</option>
          <option :value="false">Нет</option>
        </select>
      </div>
      <button class="btn save">Сохранить</button>
    </div>
  </section>
</template>
<style scoped>
.wrapper {
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 20px;
}
.card {
  background-color: #fff;
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 30px;
  border-radius: 20px;
  border: 1px solid #f0f0f5;
  transition: all 500ms ease;
  cursor: auto;
}

.card:hover,
.btn-action:hover {
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
}

h2 {
  font-weight: 600;
  color: #5b6171;
}

.btn {
  padding: 14.5px 24px;
  border-radius: 8px;
  color: #5b6171;
  font-weight: 600;
  transition: all 500ms ease;
}

.group {
  position: relative;
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.group-value {
  font-weight: 500;
  font-size: 14px;
  line-height: 16px;
  color: #5b6171;
  cursor: pointer;
}

.group-item {
  border-radius: 8px;
  padding: 12px 16px;
  border: 1px solid #dfe3ec;
  font-weight: 500;
  font-size: 14px;
  line-height: 16px;
  color: #5b6171;
}

.group-item::placeholder {
  color: #8c93a6;
  font-weight: 400;
  font-size: 14px;
  line-height: 22px;
}

.save {
  width: 100%;
  background-color: #195ee6;
  color: #fff;
  font-weight: 600;
}

h2 {
  font-size: 20px;
  font-weight: 600;
  line-height: 27.32px;
  color: #14171f;
}
.wrap-check {
  display: flex;
  align-items: center;
  gap: 10px;
}
</style>
