<script>
export default {
  name: "BusinessSettings",
  components: {},
  data() {
    return {
      junior: {
        miner: "1",
        count: "",
        sale: "",
        price: "",
      },
      middle: {
        miner: "1",
        count: "",
        sale: "",
        price: "",
      },
      senior: {
        miner: "1",
        count: "",
        sale: "",
        price: "",
      },
    };
  },
  methods: {},
};
</script>
<template>
  <section class="wrapper">
    <div class="card">
      <h2>Начинающий</h2>
      <div class="wrap-group">
        <div class="group">
          <label for="junior.miner" class="group-value">Тип аппарата</label>
          <select
            type="text"
            id="junior.miner"
            name="junior.miner"
            v-model="junior.miner"
            class="group-item"
            placeholder="Выберите роль"
          >
            <option value="1">Майнер 1</option>
          </select>
        </div>
        <div class="group">
          <label for="junior.count" class="group-value">Количество</label>
          <input
            type="text"
            id="junior.count"
            name="junior.count"
            v-model="junior.count"
            class="group-item"
            placeholder="10"
          />
        </div>
      </div>
      <div class="wrap-group">
        <div class="group">
          <label for="junior.sale" class="group-value">Скидка на хостинг</label>
          <input
            type="text"
            id="junior.sale"
            name="junior.sale"
            v-model="junior.sale"
            class="group-item"
            placeholder="5%"
          />
        </div>
        <div class="group">
          <label for="junior.price" class="group-value">Цена</label>
          <input
            type="text"
            id="junior.price"
            name="junior.price"
            v-model="junior.price"
            class="group-item"
            placeholder="5000 $"
          />
        </div>
      </div>
      <button class="btn save">Сохранить</button>
    </div>
    <div class="card">
      <h2>Продвинутый</h2>
      <div class="wrap-group">
        <div class="group">
          <label for="middle.miner" class="group-value">Тип аппарата</label>
          <select
            type="text"
            id="middle.miner"
            name="middle.miner"
            v-model="middle.miner"
            class="group-item"
            placeholder="Выберите роль"
          >
            <option value="1">Майнер 1</option>
          </select>
        </div>
        <div class="group">
          <label for="middle.count" class="group-value">Количество</label>
          <input
            type="text"
            id="middle.count"
            name="middle.count"
            v-model="middle.count"
            class="group-item"
            placeholder="10"
          />
        </div>
      </div>
      <div class="wrap-group">
        <div class="group">
          <label for="middle.sale" class="group-value">Скидка на хостинг</label>
          <input
            type="text"
            id="middle.sale"
            name="middle.sale"
            v-model="middle.sale"
            class="group-item"
            placeholder="5%"
          />
        </div>
        <div class="group">
          <label for="middle.price" class="group-value">Цена</label>
          <input
            type="text"
            id="middle.price"
            name="middle.price"
            v-model="middle.price"
            class="group-item"
            placeholder="5000 $"
          />
        </div>
      </div>
      <button class="btn save">Сохранить</button>
    </div>
    <div class="card">
      <h2>Инвестор</h2>
      <div class="wrap-group">
        <div class="group">
          <label for="senior.miner" class="group-value">Тип аппарата</label>
          <select
            type="text"
            id="senior.miner"
            name="senior.miner"
            v-model="senior.miner"
            class="group-item"
            placeholder="Выберите роль"
          >
            <option value="1">Майнер 1</option>
          </select>
        </div>
        <div class="group">
          <label for="senior.count" class="group-value">Количество</label>
          <input
            type="text"
            id="senior.count"
            name="senior.count"
            v-model="senior.count"
            class="group-item"
            placeholder="10"
          />
        </div>
      </div>
      <div class="wrap-group">
        <div class="group">
          <label for="senior.sale" class="group-value">Скидка на хостинг</label>
          <input
            type="text"
            id="senior.sale"
            name="senior.sale"
            v-model="senior.sale"
            class="group-item"
            placeholder="5%"
          />
        </div>
        <div class="group">
          <label for="senior.price" class="group-value">Цена</label>
          <input
            type="text"
            id="senior.price"
            name="senior.price"
            v-model="senior.price"
            class="group-item"
            placeholder="5000 $"
          />
        </div>
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

.wrap-avatar {
  display: flex;
  align-items: center;
  gap: 20px;
}

.container-img {
  width: 120px;
  height: 120px;
}

.container-img img {
  border-radius: 10px;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.actions-avatar {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.edit-img,
.delete-img {
  width: fit-content;
  color: #195ee6;
  text-decoration: underline;
  font-weight: 500;
  font-size: 16px;
  line-height: 21.86px;
  letter-spacing: 0em;
  cursor: pointer;
}

.delete-img {
  color: #dc2626;
}

.group-title {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.wrap-actions {
  display: flex;
  align-items: center;
  gap: 8px;
}

.new {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.wrap-actions img {
  height: 28px;
  width: 28px;
  cursor: pointer;
}

.wrap-actions span {
  font-size: 20px;
  line-height: 28px;
  font-weight: 600;
}
</style>
