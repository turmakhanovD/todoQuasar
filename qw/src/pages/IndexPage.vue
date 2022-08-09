<template>
  <q-page class="flex flex-center">
    
    <q-card class="my-card" style="width: 600px"> <!-- Создал карточку--> 
      <q-card-section>
        <div class="text-h4">To Do List</div>
      </q-card-section>

      <q-card-section>
        <div class="row justify-center"> <!--Выравнивание с помощью флексбокса-->
          <div class="col-12 q-pb-md">
             <q-input v-model="todoTask" label="Новая задача:"> <!--Поля для заполнение и добавления новых задач-->
                <template v-slot:after>
                  <q-btn round dense flat icon="send" @click="addItem" /> <!--Кнопка для добавление в массив задач-->
                </template>
             </q-input>
          </div>
        </div>
      </q-card-section>

      <q-separator />

      <q-card-section v-if="todoList.length > 0"> <!--Условие, при выполнение которого будет отображаться массив-->
        <div class="row justify-center" 
             v-for="(item, index) in todoList" :key="index"> <!--Отображаю каждый элемент моего массива todoList-->
          <div class="col-8 q-py-md">
            {{  item.value  }}
          </div>

          <div class="col-auto q-py-md">
            <q-btn round dense flat icon="done" @click="removeItem(index)" /> <!--Кнопка удаления, то есть выполнение задачи-->

          </div>

        </div>
      </q-card-section>

      <q-card-section v-else> <!--Если массив пуст, вывожу сообщение-->
        <div class="row justify-center">
          <div class="col-12">
            <div class="text-h8"> Нет задач, самое время их добавить</div>
          </div>
        </div>

      </q-card-section>


    </q-card>

  </q-page>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'IndexPage',
  data()  
  {
    return{
      todoTask: '',
      todoList:[  //Массив с данными
         { value: "Начать бегать" } ,
         { value: "Помыть посуду" }       
      ]
    }
  },
  methods: {
    addItem() { //Функция добавления в массив
      this.todoList.push({value: this.todoTask})
    },
    removeItem(index) //Функция удаления с массива
    {
      this.todoList.splice(index, 1);
    }
  }
})
</script>
