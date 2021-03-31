Пример Vue приложения с канала [Go Frontend] (https://www.youtube.com/channel/UCWhg5tJHcR22vlJ5QVz7opg)

Подключенные библиотеки
- Axios 0.19.0: https://github.com/axios/axios​
- Vuex 3.1.2: https://vuex.vuejs.org/ru/installatio...​
- Json-server (fakse-api): https://github.com/typicode/json-server​
- Node-sass 4.13.0: https://github.com/sass/node-sass​
- Sass-loader 8.0.0: https://www.npm.red/package/sass-loader​ (устанавливает так же Node-sass)


Используемые расширения для Chrome
- Vue.js devtools

Запуск приложения: 
- json-server --watch db.json
- npm run serve


Best practice:
1. Именование компонентов со смыслом и одинаковым префиксом. Пример: v-cart, v-catalog.
2. Имена компонентов в kebab-case, а при импорте в camelCase. Пример: v-cart-item, vCartItem.
3. Props всегда с типом входных данных.
props: {
    cart_item_data: {
        type: Object,
        default() {
            return {}
        }
    }
}
4. Если в элементе больше 1 атрибута - атрибуты пишем внутри тега в столбик.
      <v-cart-item 
        v-for="(item, index) in cart_data"
        :key="item.article"
        :cart_item_data="item"
        @deleteFromCart="deleteFromCart(index)"
        @increment="increment(index)"
        @decrement="decrement(index)"
      />
5. Boolean переменные начинаются с is. Пример: isElementVisible
6. Методы компонента пишутся с маленькой буквы в camelCase, а действия (методы) VUEX Uppercase.
Пример: в компоненте v-cart.vue методы increment, decrement, deleteFromCart,
    действия -   'DELETE_FROM_CART', 'INCREMENT_CART_ITEM', 'DECREMENT_CART_ITEM'
7. Разделяем actions, mutations, state и getters по отдельным файлам для лучшей навигации и восприятия данных
разбить файл store на несколько файлов в своих папках actions, getters, mutations и склеить с помощью 
- импорта import apiRequests from './actions/api-requests'
- spread оператора const actions = {...commonActions,...apiRequests}
8. Используем mapActions, mapGetters для получения и работы с данными в компонентах
за место this.$store.dispatch('GET_PRODUCTS_FROM_API') пишем в методах 
        ...mapActions([
            'GET_PRODUCTS_FROM_API'
        ]),
    не забывая импортировать
        import {mapActions} from 'vuex'
    и вызываем 
        this.GET_PRODUCTS_FROM_API()
или геттеры this.$store.state.products аналогично 
9. Объединямем родственные компоненты в папки


