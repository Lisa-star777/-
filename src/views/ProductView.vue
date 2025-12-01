<template>
  <div class="product-page">
    <!-- Хлебные крошки -->
    <section class="breadcrumb-section">
      <div class="container">
        <nav class="breadcrumb">
          <router-link to="/">Главная</router-link>
          <span class="divider">/</span>
          <router-link to="/bouquets">Букеты</router-link>
          <span class="divider">/</span>
          <span class="current">25 желтых тюльпанов</span>
        </nav>
      </div>
    </section>

    <!-- Основная информация о товаре -->
    <section class="product-main-section">
      <div class="container">
        <div class="product-layout">
          <!-- Изображение товара -->
          <div class="product-image">
            <div class="image-placeholder">
              25 желтых тюльпанов
            </div>
          </div>

          <!-- Информация о товаре -->
          <div class="product-info">
            <h1 class="product-title">25 желтых тюльпанов</h1>
            
            <div class="availability">
              <span class="available">В наличии</span>
            </div>

            <div class="product-price">
              2.500 ₽
            </div>

            <div class="product-category">
              <strong>Цветы</strong>
              <p>25 желтых тюльпанов</p>
            </div>

            <div class="product-materials">
              <strong>Материалы</strong>
              <p>Декоративный флористический материал</p>
            </div>

            <button class="order-button" @click="goToCheckout">
              ЗАКАЗАТЬ
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- Рекомендуемые товары -->
    <section class="recommended-section">
      <div class="container">
        <h2 class="recommended-title">К букету можно добавить</h2>
        
        <div class="recommended-grid">
          <div v-for="product in recommendedProducts" :key="product.id" class="recommended-card">
            <div class="recommended-badge" v-if="product.isTop">TOP</div>
            <div class="recommended-image">
              <div class="image-placeholder-small">{{ product.title }}</div>
            </div>
            <h3 class="recommended-product-title">{{ product.title }}</h3>
            <div class="recommended-price">{{ product.price }} ₽</div>
            <button class="recommended-order-button" @click="goToCheckout">
              Заказать
            </button>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'ProductView',
  data() {
    return {
      recommendedProducts: [
        { id: 1, title: '25 пионовидных роз', price: '7777', isTop: true },
        { id: 2, title: '25 пионовидных роз', price: '7777', isTop: false },
        { id: 3, title: '25 пионовидных роз', price: '7777', isTop: false },
        { id: 4, title: '25 пионовидных роз', price: '7777', isTop: false },
        { id: 5, title: '25 пионовидных роз', price: '7777', isTop: false }
      ]
    }
  },
  methods: {
    goToCheckout() {
      this.$router.push('/checkout')
    }
  }
}
</script>


<style scoped>
.product-page {
  margin-top: 120px;
  min-height: 100vh;
  background-color: #ffffff;
}

/* Хлебные крошки */
.breadcrumb-section {
  background-color: #ffffff;
  padding: 20px 0;
  border-bottom: 1px solid #e0e0e0;
}

.breadcrumb {
  display: flex;
  align-items: center;
  gap: 10px;
  font-family: 'Albert Sans', sans-serif;
  font-size: 14px;
}

.breadcrumb a {
  color: #666;
  text-decoration: none;
  transition: color 0.3s ease;
}

.breadcrumb a:hover {
  color: #292966;
}

.breadcrumb .current {
  color: #292966;
  font-weight: 600;
}

.breadcrumb .divider {
  color: #999;
}

/* Основная секция товара */
.product-main-section {
  padding: 50px 0;
  background-color: #ffffff;
}

.product-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: start;
}

.product-image {
  width: 100%;
  background-color: #B8B8B8;
  border-radius: 12px;
  overflow: hidden;
  aspect-ratio: 1/1;
}

.image-placeholder {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-family: 'Albert Sans', sans-serif;
  font-size: 24px;
  font-weight: 600;
  background-color: #A3A3CC;
}

.product-info {
  padding: 20px 0;
}

.product-title {
  font-family: 'Albert Sans', sans-serif;
  font-size: 32px;
  color: #292966;
  margin-bottom: 20px;
  font-weight: 600;
  line-height: 1.3;
}

.availability {
  margin-bottom: 20px;
}

.available {
  background-color: #4CAF50;
  color: white;
  padding: 8px 16px;
  border-radius: 20px;
  font-family: 'Albert Sans', sans-serif;
  font-size: 14px;
  font-weight: 600;
}

.product-price {
  font-family: 'Russo One', sans-serif;
  font-size: 48px;
  color: #292966;
  margin-bottom: 30px;
  font-weight: bold;
}

.product-category,
.product-materials {
  margin-bottom: 25px;
}

.product-category strong,
.product-materials strong {
  font-family: 'Albert Sans', sans-serif;
  font-size: 18px;
  color: #292966;
  display: block;
  margin-bottom: 8px;
  font-weight: 600;
}

.product-category p,
.product-materials p {
  font-family: 'Albert Sans', sans-serif;
  font-size: 16px;
  color: #666;
  margin: 0;
  line-height: 1.5;
}

.order-button {
  background-color: #292966;
  color: white;
  border: none;
  padding: 20px 40px;
  border-radius: 10px;
  font-family: 'Albert Sans', sans-serif;
  font-weight: 700;
  font-size: 18px;
  cursor: pointer;
  transition: all 0.3s ease;
  width: 100%;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.order-button:hover {
  background-color: #1a1a4d;
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(41, 41, 102, 0.3);
}

/* Секция рекомендованных товаров */
.recommended-section {
  padding: 60px 0;
  background-color: #f8f9fa;
  border-top: 3px solid #292966;
}

.recommended-title {
  font-family: 'Albert Sans', sans-serif;
  font-size: 28px;
  color: #292966;
  margin-bottom: 40px;
  text-align: center;
  font-weight: 600;
}

.recommended-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 20px;
}

.recommended-card {
  background-color: #B8B8B8;
  border-radius: 12px;
  padding: 20px;
  text-align: center;
  position: relative;
  transition: all 0.3s ease;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
}

.recommended-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

.recommended-badge {
  position: absolute;
  top: -10px;
  left: 50%;
  transform: translateX(-50%);
  background-color: #292966;
  color: white;
  padding: 5px 15px;
  border-radius: 15px;
  font-family: 'Albert Sans', sans-serif;
  font-size: 12px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.recommended-image {
  width: 100%;
  height: 120px;
  background-color: #A3A3CC;
  border-radius: 8px;
  margin-bottom: 15px;
  overflow: hidden;
}

.image-placeholder-small {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-family: 'Albert Sans', sans-serif;
  font-size: 12px;
  font-weight: 600;
  text-align: center;
  padding: 10px;
}

.recommended-product-title {
  font-family: 'Albert Sans', sans-serif;
  font-weight: 600;
  font-size: 14px;
  margin-bottom: 10px;
  color: #292966;
  line-height: 1.3;
  min-height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.recommended-price {
  font-family: 'Albert Sans', sans-serif;
  font-weight: 700;
  font-size: 18px;
  color: #292966;
  margin-bottom: 15px;
}

.recommended-order-button {
  background-color: #A3A3CC;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 6px;
  font-family: 'Albert Sans', sans-serif;
  font-weight: 600;
  font-size: 14px;
  cursor: pointer;
  transition: all 0.3s ease;
  width: 100%;
}

.recommended-order-button:hover {
  background-color: #9292c2;
  transform: translateY(-2px);
}

/* Модальное окно контактов */
.contacts-modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2000;
  backdrop-filter: blur(5px);
}

.modal-content {
  background-color: white;
  padding: 40px;
  border-radius: 15px;
  max-width: 500px;
  width: 90%;
  position: relative;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
}

.close-button {
  position: absolute;
  top: 15px;
  right: 20px;
  background: none;
  border: none;
  font-size: 30px;
  cursor: pointer;
  color: #666;
  transition: color 0.3s ease;
}

.close-button:hover {
  color: #292966;
}

.modal-content h3 {
  font-family: 'Albert Sans', sans-serif;
  font-size: 24px;
  color: #292966;
  margin-bottom: 25px;
  text-align: center;
  font-weight: 600;
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: 15px;
  margin-bottom: 25px;
}

.contact-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px 0;
  border-bottom: 1px solid #f0f0f0;
}

.contact-label {
  font-family: 'Albert Sans', sans-serif;
  font-weight: 600;
  color: #292966;
  font-size: 14px;
}

.contact-value {
  font-family: 'Albert Sans', sans-serif;
  color: #666;
  font-size: 16px;
  text-align: right;
}

.modal-note {
  font-family: 'Albert Sans', sans-serif;
  font-size: 14px;
  color: #666;
  text-align: center;
  font-style: italic;
  margin-top: 20px;
}

/* Адаптивность */
@media (max-width: 1200px) {
  .recommended-grid {
    grid-template-columns: repeat(4, 1fr);
  }
}

@media (max-width: 992px) {
  .product-layout {
    grid-template-columns: 1fr;
    gap: 40px;
  }
  
  .recommended-grid {
    grid-template-columns: repeat(3, 1fr);
  }
  
  .product-title {
    font-size: 28px;
  }
  
  .product-price {
    font-size: 40px;
  }
}

@media (max-width: 768px) {
  .product-page {
    margin-top: 140px;
  }
  
  .recommended-grid {
    grid-template-columns: repeat(2, 1fr);
  }
  
  .product-title {
    font-size: 24px;
  }
  
  .product-price {
    font-size: 36px;
  }
  
  .recommended-title {
    font-size: 24px;
  }
  
  .modal-content {
    padding: 30px 25px;
  }
}

@media (max-width: 480px) {
  .product-page {
    margin-top: 160px;
  }
  
  .recommended-grid {
    grid-template-columns: 1fr;
    max-width: 300px;
    margin: 0 auto;
  }
  
  .product-title {
    font-size: 20px;
  }
  
  .product-price {
    font-size: 32px;
  }
  
  .order-button {
    padding: 16px 30px;
    font-size: 16px;
  }
  
  .contact-item {
    flex-direction: column;
    align-items: flex-start;
    gap: 5px;
  }
  
  .contact-value {
    text-align: left;
  }
}
</style>