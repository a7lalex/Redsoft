<template>
  <div id="app">
    <div class="header">
      <a href=""><img src="./assets/image/logo-top.svg" alt="logo-top.svg"></a>
      <ul class="menu">
        <li v-for="item in menu" :key="item.name" class="menu__item"><a :href="item.link" class="menu__link">{{item.name}}</a></li>
      </ul>
      <form action="" class="search">
        <input type="text" class="search__input">
        <button type="submit" class="btn">Найти</button>
      </form>
    </div>
    <div class="main">
      <h1>Картины эпохи Возрождения</h1>
      <div class="card" v-for="item in catalog" :key="item.name">
        <img :src="item.img" :alt="item.img" class="card__img">
        <div class="card__head">{{item.name}}</div>
        <div v-if="true" class="card__bottom">
          <div v-if="item.sale" class="card__sale">{{item.sale}}</div>
          <div class="card__price">{{item.price}}</div>
          <button class="btn">Купить</button>
        </div>
        <div v-if="false" class="card__bottom">
          Продана на аукционе
        </div>
      </div>
    </div>
    <div class="footer">
      <a href=""><img src="./assets/image/logo-bot.svg" alt="logo-bot.svg"></a>
      <ul class="menu">
        <li v-for="item in menu" :key="item.name" class="menu__item"><a :href="item.link" class="menu__link">{{item.name}}</a></li>
      </ul>
      <div class="footer__phone">
        <img src="./assets/image/phone.svg" alt="phone.svg">
        <span>{{phone}}</span>
      </div>
      <div class="footer__adress">
        <img src="./assets/image/adress.svg" alt="adress.svg">
        <span>{{adress}}</span>
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
      phone: '+7 (495) 555-55-55',
      adress: 'г. Москва, ул. Расплетина, 24',
      catalog:[
        {
          name: '«Рождение Венеры» Сандро Боттичелли',
          sale: '2 000 000 $',
          price: '1 000 000 $',
          img: require('./assets/image/1.jpg')
        },
        {
          name: '«Тайная вечеря»  Леонардо да Винчи',
          sale: '',
          price: '3 000 000 $',
          img: require('./assets/image/2.jpg')
        },
        {
          name: '«Сотворение Адама» Микеланджело',
          sale: '6 000 000 $',
          price: '5 000 000 $',
          img: require('./assets/image/3.jpg')
        },
        {
          name: '«Урок анатомии»  Рембрандт',
          sale: '',
          price: '4 000 000 $',
          img: require('./assets/image/4.jpg')
        },
      ]
    }
  },
}
</script>
