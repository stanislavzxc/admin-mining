<script>
export default {
  name: "MailSettings",
  components: {},
  data() {
    return {
      count: 1,
      mails: [
        {
          name: "",
          template: "",
        },
      ],
    };
  },
  methods: {
    plus() {
      try {
        this.mails.push({
          name: "",
          template: "",
        });
        this.count++;
      } catch (err) {
        console.log(err);
      }
    },

    minus() {
      try {
        if (this.count != 1) {
          this.mails.pop();
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
        <h2>Шаблоны писем</h2>
        <div class="wrap-actions">
          <img @click="minus" src="../../assets/minus.png" alt="" />
          <span>{{ count }}</span>
          <img @click="plus" src="../../assets/plus.png" alt="" />
        </div>
      </div>
      <div class="mail" v-for="(item, i) in mails" :key="i">
        <div class="group">
          <label for="mail" class="group-value"
            >Название шаблона {{ i + 1 }}</label
          >
          <input
            type="text"
            id="mail"
            name="mail"
            v-model="item.name"
            class="group-item"
            placeholder="Название"
          />
        </div>
        <div class="group">
          <label for="template" class="group-value">Шаблон {{ i + 1 }}</label>
          <input
            type="text"
            id="template"
            name="template"
            v-model="item.template"
            class="group-item"
            placeholder="HTML код"
          />
        </div>
        <div class="hr"></div>
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

.mail {
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
