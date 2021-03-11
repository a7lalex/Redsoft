<template>
  <div id="app">
    <div class="header">
      <img src="./assets/image/logo-top.svg" alt="logo-top.svg">
      <ul class="menu">
        <li class="menu__item"><a href="" class="menu__link">Каталог</a></li>
        <li class="menu__item"><a href="" class="menu__link">Доставка</a></li>
      </ul>
      <form action="" class="search">
        <input type="text" class="search__input">
        <button type="submit" class="btn">Найти</button>
      </form>
    </div>
    <div class="main">
      <h1>Картины эпохи Возрождения</h1>
      <div class="card">
        <img src="./assets/image/1.jpg" alt="1.jpg" class="card__img">
        <div class="card__head">«Рождение Венеры» Сандро Боттичелли</div>
        <div class="card__bottom">
          <div class="card__sale">2 000 000 $</div>
          <div class="card__price">1 000 000 $</div>
          <button class="btn">Купить</button>
        </div>
      </div>
    </div>
    <div class="footer">
      <img src="./assets/image/logo-bot.svg" alt="logo-bot.svg">
      <ul class="menu">
        <li class="menu__item"><a href="" class="menu__link">Каталог</a></li>
        <li class="menu__item"><a href="" class="menu__link">Доставка</a></li>
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
      phone: '+7 (495) 555-55-55',
      adress: 'г. Москва, ул. Расплетина, 24',
      catalog:[
        {
          name: '«Рождение Венеры» Сандро Боттичелли',
          sale: '2 000 000 $',
          price: '1 000 000 $',
          img: '1'
        },
        {
          name: '«Тайная вечеря»  Леонардо да Винчи',
          sale: '',
          price: '3 000 000 $',
          img: '2'
        },
        {
          name: '«Сотворение Адама» Микеланджело',
          sale: '6 000 000 $',
          price: '5 000 000 $',
          img: '3'
        },
        {
          name: '«Урок анатомии»  Рембрандт',
          sale: '',
          price: '4 000 000 $',
          img: '4'
        },
      ]
    }
  },
}
</script>
