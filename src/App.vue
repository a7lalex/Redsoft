<template>
  <div id="app">
    <div class="header">
      <div class="container">
        <div class="container__nav">
          <a href=""><img class="container__logo" src="./assets/image/logo-top.svg" alt="logo-top.svg"></a>
          <ul class="menu">
            <li v-for="item in menu" :key="item.name" class="menu__item"><a :href="item.link" class="menu__link">{{item.name}}</a></li>
          </ul>
        </div>
        <form action="" class="search">
          <input type="text" class="search__input" placeholder="Поиск по названию картины">
          <button type="submit" class="btn">Найти</button>
        </form>
      </div>
    </div>
    <div class="main">
      <h1 class="main__header">Картины эпохи Возрождения</h1>
      <div class="container container-main">
        <div class="card" :class="{ 'card-null': item.quantity == 0}" v-for="item in catalog" :key="item.name" >
          <img :src="item.img" :alt="item.img">
          <div class="card__head">{{item.name}}</div>
          <div v-if="item.quantity != 0" class="card__bottom">
            <div class="card__price">
              <div v-if="item.sale" class="card__sale">{{item.sale}}</div>
              <div>{{item.price}}</div>
            </div>
            <button @click="buyProduct(item)" class="btn">
              <div v-if="!item.basket" :class="{ 'loader': item.anime }">Купить</div>
              <div v-if="item.basket" class="card__basket" :class="{ 'loader': item.anime }"><img src="./assets/image/check.svg" alt="">В корзине</div>
            </button>
          </div>
          <div v-if="item.quantity == 0" class="card__bottom card__bottom-null">
            Продана на аукционе
          </div>
        </div>
      </div>
    </div>
    <div class="footer">
      <div class="container">
        <div class="container__nav">
          <a href=""><img class="container__logo" src="./assets/image/logo-bot.svg" alt="logo-bot.svg"></a>
          <ul class="menu menu-footer">
            <li v-for="item in menu" :key="item.name" class="menu__item"><a :href="item.link" class="menu__link">{{item.name}}</a></li>
          </ul>
        </div>
        <a class="footer__link" :href="phone.link">
          <img src="./assets/image/phone.svg" alt="phone.svg">
         {{phone.number}}
        </a>
        <a class="footer__link" :href="adress.link">
          <img src="./assets/image/adress.svg" alt="adress.svg">
          <span>{{adress.title}}</span>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      menu: [{
        name: 'Каталог',
        link: ''
      },
      {
        name: 'Доставка',
        link: ''
      },
      {
        name: 'Оплата',
        link: ''
      },
      {
        name: 'Контакты',
        link: ''
      },
       {
        name: 'О галерее',
        link: ''
      }],
      phone: {
        link: 'tel:+74955555555',
        number: '+7 (495) 555-55-55'
      },
      adress: {
        link: 'https://yandex.ru/maps/-/CCUQjGqrxD',
        title: 'г. Москва, ул. Расплетина, 24'
      },
      catalog:[
        {
          name: '«Рождение Венеры» Сандро Боттичелли',
          sale: '2 000 000 $',
          price: '1 000 000 $',
          img: require('./assets/image/1.jpg'),
          quantity: '1',
          basket: false,
          anime: false
        },
        {
          name: '«Тайная вечеря»  Леонардо да Винчи',
          sale: '',
          price: '3 000 000 $',
          img: require('./assets/image/2.jpg'),
          quantity: '1',
          basket: false,
          anime: false
        },
        {
          name: '«Сотворение Адама» Микеланджело',
          sale: '6 000 000 $',
          price: '5 000 000 $',
          img: require('./assets/image/3.jpg'),
          quantity: '1',
          basket: true,
          anime: false
        },
        {
          name: '«Урок анатомии»  Рембрандт',
          sale: '',
          price: '4 000 000 $',
          img: require('./assets/image/4.jpg'),
          quantity: '0',
          basket: false,
          anime: false
        },
      ]
    }
  },
  mounted() {
    if (window.localStorage.catalog) {
      this.catalog = JSON.parse(window.localStorage.getItem('catalog'))
    }
  },
  methods: {
    // Добавляет в корзину
    buyProduct: function (elem) {
      let _this = this
      let localStorage = window.localStorage
      let url = 'https://jsonplaceholder.typicode.com/posts/1';
      elem.anime = true

      setTimeout(function(){
        fetch(url)
          .then((response) => {
            return response.json();
          })
          .then((data) => {
            elem.anime = false
            elem.basket = !elem.basket;
            localStorage.setItem('catalog', JSON.stringify(_this.catalog))
            console.log(data);
          })
      }, 1000);
    },
  }
}
</script>
