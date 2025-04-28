<script>
import axios from 'axios'
export default {
  name: "AppMiner",
  components: {},
  data() {
    return {
      id: this.$route.params.id,
      name: "",
      rang: '',
      show: null,
      desc: "",
      category: "",
      hash: "",
      energy_consumption: "",
      price: "",
      image: "",
      count_sale: '',
      sale: '',
      id_client: "",
      count_client: '',
      sale_client: '',
    };
  },
  methods: {
    async getMiners() {
      const url = `/miners/${this.id}/`;
      const headers = {
        "Authorization": `Bearer ${localStorage.getItem('token')}`
      };

      try {
        const response = await axios.get(url, { headers });

        const miner = response.data.miner_item;
      
        const image = response.data.miner_item.image || 'Нет данных';
       
        this.name = miner.name || 'Нет данных';
        this.rang = miner.priority || 'Нет данных';
        this.show = miner.is_hidden || 'Нет данных';
        this.desc = miner.description || 'Нет данных';
        this.categories = response.data.categories || [];
        const currentCategory = miner.category || {};
        this.category = currentCategory.name;
        this.hash = miner.hash_rate_str || 'Нет данных';
        this.energy_consumption = miner.energy_consumption || 'Нет данных';
        this.price = miner.price || 'Нет данных';
        this.image = image.url || 'Нет данных';
        // this.image_id = image.url || 'Нет данных';

        this.count_sale = miner.discount_count || 'Нет данных';
        this.sale = miner.discount_value || 'Нет данных';
        console.log(response.data)
      } catch (error) {
        console.error("Error fetching users:", error);
      }
    },
    async update() {
  const url = `/miners/${this.id}`;
  const headers = {
    "Authorization": `Bearer ${localStorage.getItem('token')}`,
  };

  const data = new FormData();
  data.append('name', this.name);
  data.append('description', this.desc);
  data.append('category', this.category);
  data.append('hash_rate', this.hash);
  data.append('energy_consumption', this.energy_consumption);
  data.append('price', this.price);
  data.append('priority', this.rang);
  data.append('ishidden', this.show );

  try {
    const response = await axios.post(url, data, { headers });
    console.log(response);
  } catch (error) {
    console.error("Error fetching users:", error);
  }
},

    async deleteMiners(){
      const url = `/miners/${this.id}/delete`;
      const headers = {
        "Authorization": `Bearer ${localStorage.getItem('token')}`
      };
      try {
        const response = await axios.post(url,{ headers });
        console.log(response)
         
      } catch (error) {
        console.error("Error fetching users:", error);
      }
    }
  },
  mounted(){
    this.getMiners();
  }
};
</script>
<template>
  <section class="wrapper">
    <div class="group-title">
      <h1>Майнер #{{ id }}</h1>
      <button class="btn edit">Редактиовать</button>
    </div>
    <div class="card">
      <h2>Общая информация</h2>
      <div class="wrap-group">
        <div class="group">
          <label for="name" class="group-value">Название</label>
          <input
            type="text"
            id="name"
            name="name"
            v-model="name"
            class="group-item"
            placeholder="Введите название"
          />
        </div>
        <div class="group">
          <label for="rang" class="group-value">Приоритет</label>
          <input
            type="text"
            id="rang"
            name="rang"
            v-model="rang"
            class="group-item"
            placeholder="Введите приоритет"
          />
        </div>
      </div>
      <div class="group">
        <label for="desc" class="group-value">Описание</label>
        <input
          type="text"
          id="desc"
          name="desc"
          v-model="desc"
          class="group-item"
          placeholder="Введите описание"
        />
      </div>
      <div class="wrap-check">
        <input type="checkbox" v-model="closed" id="closed" class="checkbox" />
        <label for="closed" class="group-value">Скрыть</label>
      </div>
      <div class="group">
  <label for="category" class="group-value">Категория</label>
  <select class="group-item" name="category" id="category" v-model="category">
    <option v-for="cat in categories" :key="cat.id" :value="cat.name">{{ cat.name }}</option>
  </select>
</div>
      <div class="wrap-group">
        <div class="group">
          <label for="hash" class="group-value">Хешрейт (TH/s)</label>
          <input
            type="text"
            id="hash"
            name="hash"
            v-model="hash"
            class="group-item"
            placeholder="Введите хешрейт"
          />
        </div>
        <div class="group">
          <label for="energy_consumption" class="group-value"
            >Энергопотребление (W)</label
          >
          <input
            type="text"
            id="energy_consumption"
            name="energy_consumption"
            v-model="energy_consumption"
            class="group-item"
            placeholder="Введите энергопотребление"
          />
        </div>
      </div>
      <div class="group">
        <label for="price" class="group-value">Цена (USD)</label>
        <input
          type="text"
          id="price"
          name="price"
          v-model="price"
          class="group-item"
          placeholder="Введите цену"
        />
      </div>
      <div class="wrap-avatar">
  <div class="container-img">
    <img :src="image ? image : '../assets/image.png'" alt="Майнер" />
  </div>
  <div class="actions-avatar">
    <a class="edit-img">Изменить</a>
    <a class="delete-img">Удалить</a>
  </div>
</div>
    </div>
    <div class="card">
      <h2>Скидки</h2>
      <div class="wrap-group">
        <div class="group">
          <label for="count_sale" class="group-value"
            >Количество для скидки</label
          >
          <input
            type="text"
            id="count_sale"
            name="count_sale"
            v-model="count_sale"
            class="group-item"
            placeholder="Введите хешрейт"
          />
        </div>
        <div class="group">
          <label for="sale" class="group-value">Процент скидки</label>
          <input
            type="text"
            id="sale"
            name="sale"
            v-model="sale"
            class="group-item"
            placeholder="Введите энергопотребление"
          />
        </div>
        <button class="delete-img">Удалить</button>
      </div>
      <button class="edit-img">Добавить</button>
    </div>
    <div class="card">
      <h2>Добавить в корзину клиента</h2>
      <div class="wrap-group">
        <div class="group">
          <label for="id_client" class="group-value">ID Клиента</label>
          <input
            type="text"
            id="id_client"
            name="id_client"
            v-model="id_client"
            class="group-item"
            placeholder="Введите ID клиента"
          />
        </div>
        <div class="group">
          <label for="count_client" class="group-value">Количество</label>
          <input
            type="text"
            id="count_client"
            name="count_client"
            v-model="count_client"
            class="group-item"
            placeholder="Введите количество"
          />
        </div>
        <div class="group">
          <label for="sale_client" class="group-value">Скидки</label>
          <input
            type="text"
            id="sale_client"
            name="sale_client"
            v-model="sale_client"
            class="group-item"
            placeholder="Введите скидки"
          />
        </div>
      </div>
      <button class="btn send">Отправить</button>
    </div>
    <div class="wrap-btns">
      <button class="btn delete" @click="deleteMiners()">Удалить</button>
      <button class="btn save" @click="update()">Сохранить</button>
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

.wrap-title {
  display: flex;
  align-items: center;
  gap: 8px;
}

.group-title {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

h1 span {
  font-weight: 600;
  font-size: 24px;
  line-height: 32.78px;
}

h2 {
  font-size: 20px;
  font-weight: 600;
  line-height: 27.32px;
  color: #14171f;
}

.btn {
  padding: 14.5px 24px;
  border-radius: 8px;
  color: #5b6171;
  font-weight: 600;
  transition: all 500ms ease;
}
.edit {
  color: #195ee6;
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

.info {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.info-item {
  display: flex;
  align-items: center;
  gap: 10px;
}

.info-title {
  display: flex;
  align-items: center;
  gap: 10px;
  font-weight: 500;
  color: #5b6171;
}

.info-value {
  font-weight: 500;
  color: #262d40;
  font-size: 16px;
  line-height: 21.86px;
  letter-spacing: 0em;
  color: #262d40;
}
.wrap-check {
  display: flex;
  align-items: center;
  gap: 10px;
}

.send {
  background-color: #195ee6;
  font-weight: 600;
  letter-spacing: 0em;
  color: #fff;
}

.wrap-btns {
  display: flex;
  align-items: center;
  background-color: #fff;
  gap: 20px;
  padding: 30px;
  border-radius: 20px;
  border: 1px solid #f0f0f5;
  transition: all 500ms ease;
  cursor: auto;
}

.save {
  width: 100%;
  background-color: #195ee6;
  color: #fff;
  font-weight: 600;
}

.delete {
  width: 100%;
  background-color: #dc2626;
  color: #fff;
  font-weight: 600;
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
</style>
