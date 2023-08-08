<script>
export default {
  data() {
    return {
      children: []
    }
  },
  methods: {
    addForm() {
      this.children.push({ name: 'Имя', age: 'Возраст' });
    },
    removeForm(index) {
      this.children.splice(index, 1);
    },
    saveData() {
      // Собираем все данные в объект
      const formData = {
        name: this.name,
        age: this.age,
        children: this.children
      }
      this.$router.push({
        path: `about/${formData.name}/${formData.age}/${JSON.stringify(formData.children)}`
      });
  }
}
}
</script>

<template>
  <div class="home">
    <div class="text">Персональные данные</div>
    <label  for="name">Имя</label>
      <input type="text" v-model="name" name="name" >
    <label for="age">Возраст</label>
      <input name="age" v-model="age" type="text" >
  </div>
  <div class="home_view">
    <div class="text">Дети: {{ children.length }}</div>
    <div class="btn_add" @click="addForm">
          <svg class="plus" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none">
              <path fill-rule="evenodd" clip-rule="evenodd" d="M5.13332 10.8556C4.50125 10.8555 3.98887 11.3679 3.98887 12C3.98887 12.6321 4.50126 13.1445 5.13332 13.1445L10.8554 13.1445L10.8554 18.8668C10.8554 19.4989 11.3678 20.0113 11.9999 20.0113C12.632 20.0113 13.1444 19.4989 13.1444 18.8668L13.1443 13.1445L18.8667 13.1445C19.4988 13.1445 20.0112 12.6321 20.0112 12C20.0112 11.3679 19.4988 10.8556 18.8667 10.8556L13.1443 10.8556L13.1443 5.13338C13.1443 4.50132 12.632 3.98893 11.9999 3.98893C11.3678 3.98893 10.8554 4.50131 10.8554 5.13338L10.8554 10.8556L5.13332 10.8556Z" fill="#01A7FD"/>
          </svg>
    Добавить ребенка</div>
  </div>
  <div v-for="(child, index) in children" :key="index" class="form_flex">
    
      <input v-model="child.name" name="name" class="children" type="text">
      
      <input v-model="child.age"  name="age" class="children" type="text">
      <div class="remove" @click="removeForm(index)">удалить</div>
  </div>
  <div class="save"  v-if="children.length > 0" @click="saveData">Сохранить</div>
</template>



<style scoped>
  .home{
    width: 616px;
    height: 166px;
  }

  .plus{
    position: absolute;
    left: 13px;
  }

  .save{
    display: inline-flex;
    padding: 10px 20px;
    flex-direction: column;
    align-items: center;
    border-radius: 100px;
    background: var(--colors-primary, #01A7FD);
    color: white;
  }

  .text{
    color: var(--colors-black, #111);
    /* 16 Paragraph 2 Medium */
    font-family: Montserrat;
    font-size: 16px;
    font-style: normal;
    font-weight: 500;
    line-height: 24px; /* 150% */
  }

  input{
    display: flex;
    width: 616px;
    height: 56px;
    justify-content: center;
    align-items: center;
    flex-shrink: 0;
    border: 1px solid #F1F1F1;
  }

  label{
    color: var(--colors-gray, rgba(17, 17, 17, 0.48));
    /* 13 Paragraph 3 */
    font-family: Montserrat;
    font-size: 13px;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
    position: relative;
    top: 20px;
    left:10px;
  }

  .home_view{
    position: relative;
    top: 54px;
    width: 616px;
    height: 166px;
  }

  #label_name{
    position: relative;
    left: 20px;
  }

  .btn_add{
    display: inline-flex;
    padding: 10px 20px;
    flex-direction: column;
    align-items: center;
    width: 204px;
    height: 44px;
    border-radius: 100px;
    border: 2px solid var(--colors-primary, #01A7FD);
    color: #01A7FD;
    position: relative;
    left: 404px;
    bottom: 33px;
  }

  .children{
    width: 260px;
    height: 56px;
    justify-content: center;
    align-items: center;
    flex-shrink: 0;
    border: 1px solid #F1F1F1;
  }

  .form_flex{
    display: flex;
    align-items: center;
    gap: 18px;
    margin-bottom: 10px;
  }

  .remove{
    color: var(--colors-primary, #01A7FD);
    /* 16 Paragraph 2 */
    font-family: Montserrat;
    font-size: 14px;
    font-style: normal;
    font-weight: 400;
    line-height: 24px; /* 171.429% */
  }

</style>