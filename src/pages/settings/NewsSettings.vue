<script>
export default {
  name: "NewsSettings",
  components: {},
  data() {
    return {
      count: 1,
      news: [
        {
          new: "",
          img: "",
          title: "",
          desc: "",
        },
      ],
    };
  },
  methods: {
    plus() {
      try {
        this.news.push({
          new: "",
          img: "",
          title: "",
          desc: "",
        });
        this.count++;
      } catch (err) {
        console.log(err);
      }
    },

    minus() {
      try {
        if (this.count != 1) {
          this.news.pop();
          this.count--;
        }
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>
<template>
  <section class="wrapper">
    <div class="card">
      <div class="group-title">
        <h2>Новости</h2>
        <div class="wrap-actions">
          <img @click="minus" src="../../assets/minus.png" alt="" />
          <span>{{ count }}</span>
          <img @click="plus" src="../../assets/plus.png" alt="" />
        </div>
      </div>
      <div class="new" v-for="(item, i) in news" :key="i">
        <div class="group">
          <label for="new" class="group-value">Новость {{ i + 1 }}</label>
          <input
            type="text"
            id="new"
            name="new"
            v-model="item.new"
            class="group-item"
            placeholder="Link"
          />
        </div>
        <div class="wrap-group">
          <div class="group">
            <label for="title" class="group-value">Заголовок</label>
            <input
              type="text"
              id="title"
              name="title"
              v-model="item.title"
              class="group-item"
              placeholder="Заголовок"
            />
          </div>
          <div class="group">
            <label for="desc" class="group-value">Описание</label>
            <input
              type="text"
              id="desc"
              name="desc"
              v-model="item.desc"
              class="group-item"
              placeholder="Описание"
            />
          </div>
        </div>
        <div class="wrap-avatar">
          <div class="container-img">
            <img src="../../assets/image.png" alt="" />
          </div>
          <div class="actions-avatar">
            <a class="edit-img">Изменить</a>
            <a class="delete-img">Удалить</a>
          </div>
        </div>
      </div>
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
