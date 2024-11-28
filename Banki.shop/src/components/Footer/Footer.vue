<template>
  <footer class="footer">
    <div class="container">
      <nav class="footer__nav">
        <li class="footer__nav-item">Каталог</li>
        <li class="footer__nav-item">Доставка</li>
        <li class="footer__nav-item">Оплата</li>
        <li class="footer__nav-item">Контакты</li>
        <li class="footer__nav-item">О компании</li>
      </nav>
      <address class="footer__info">
        <span class="footer__info-phone"
          ><img :src="require('../../public/phone.png')" alt="Phone icon" />+7
          (812) 555-55-55</span
        >
        <span class="footer__info-address"
          ><img
            :src="require('../../public/address.png')"
            alt="Address icon"
          />г. Санкт-Петербург, ул. Ефимова, 3</span
        >
      </address>
    </div>
  </footer>
</template>

<script>
import './footer.css';
export default {
  name: 'PageFooter',
};
</script>
