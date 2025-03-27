<template>
  <div class="valentine-landing">
    <!-- Header Mejorado -->
    <header class="header-animated">
      <div class="floating-hearts">❤</div>
      <h1> TE VOY A EXTRAÑAR CUY 🥺 </h1>
      <p class="subtitle-animated">Un pequeño espacio para recordarte lo especial que eres.</p>
      <div class="sparkles">✨</div>
    </header>

    <!-- Sección de Mensajes Mejorada -->
    <section class="messages">
      <h2>Mensajes para ti</h2>
      <div class="message-container">
        <div class="message bounce-animation">
          <p>¡Eres la mejor persona que alguien podría desear! Gracias por siempre estar ahí. 💌</p>
        </div>
        <div class="message bounce-animation">
          <p>En este día de la amistad, quiero recordarte lo increíble que eres. ¡Te quiero mucho! CUY️</p>
        </div>
        <div class="message bounce-animation">
          <p>Gracias por todas las risas compartidas y los momentos inolvidables 🌟</p>
        </div>
        <div class="message bounce-animation">
          <p>Tu amistad es uno de los regalos más valiosos que tengo 🎁</p>
        </div>
      </div>
    </section>

    <!-- Sección de Fotos Mejorada -->
    <section class="photos">
      <h2>Cada foto oculta un mensaje :)</h2>
      <div class="photo-grid">
        <div class="photo-container" @click="showMessage('¡Ilumina todos tus dias! 🌞')">
          <img src="https://res.cloudinary.com/drkelnilg/image/upload/v1739424812/imagen_2025-02-13_003330902_wnlwgh.png" alt="Foto 1" />
          <div class="photo-overlay">
            <span>Click para ver mensaje especial</span>
          </div>
        </div>
        <div class="photo-container" @click="showMessage('¡Eres una amiga increíble! 🌈')">
          <img src="https://res.cloudinary.com/drkelnilg/image/upload/v1739424965/imagen_2025-02-13_003605587_z1lj3h.png" alt="Foto 2" />
          <div class="photo-overlay">
            <span>Click para ver mensaje especial</span>
          </div>
        </div>
        <div class="photo-container" @click="showMessage('¡Gracias por perimitirme ser ser parte de un pedacito de tu vida! 💫')">
          <img src="https://res.cloudinary.com/drkelnilg/image/upload/v1739425072/imagen_2025-02-13_003752060_xahin4.png" alt="Foto 3" />
          <div class="photo-overlay">
            <span>Click para ver mensaje especial</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Nueva Sección de Recuerdos -->
    <section class="special-moments">
      <h2>Momentos Especiales ✨</h2>
      <carousel class="custom-carousel" :autoplay="0" :wrap-around="true" :show-arrows="true" :show-dots="true">
        <slide v-for="(moment, index) in moments" :key="index">
          <div v-if="moment.type === 'photo'" class="moment-item">
            <img :src="moment.src" :alt="moment.alt" class="moment-image" />
            <p class="moment-caption">{{ moment.caption }}</p>
          </div>
          <div v-else-if="moment.type === 'video'" class="moment-item">
            <video :src="moment.src" controls class="moment-video"></video>
            <p class="moment-caption">{{ moment.caption }}</p>
          </div>
        </slide>
      </carousel>
    </section>

    <section class="dedicated-song">
      <h4>Canción Dedicada 🎵</h4>
      <p>Esta cancion me gusto jeje y pos pense en dejartela por aqui, espero te guste :)</p>
      <audio controls>
        <source src="https://res.cloudinary.com/drkelnilg/video/upload/v1739502377/WhatsApp_Audio_2025-02-13_at_10.03.40_PM_hhkwfu.m4a" type="audio/mpeg">
        Tu navegador no soporta el elemento de audio.
      </audio>
    </section>

    <!-- Footer Mejorado -->
    <footer>
      <h4>Hecho con mucho cariño para Cuy 💝</h4>
      <h6>No te aburras de mi :) porque nunca te dejare de molestar jeje 😁</h6>
    </footer>

    <!-- Modal para Mensajes -->
    <div v-if="showModal" class="message-modal" @click="showModal = false">
      <div class="modal-content">
        <p>{{ currentMessage }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import { Carousel, Slide } from 'vue3-carousel';
import 'vue3-carousel/dist/carousel.css';

export default {
  name: "ValentineLanding",
  components: {
    Carousel,
    Slide,
  },
  data() {
    return {
      showModal: false,
      currentMessage: '',
      messages: [],
      moments: [
        {
          type: 'photo',
          src: 'https://res.cloudinary.com/drkelnilg/image/upload/v1739428380/imagen_2025-02-13_013258963_siiqib.png',
          alt: 'Foto 1',
          caption: 'El dia que me vi esa peli por tu videollamda',
        },
        {
          type: 'video',
          src: 'https://res.cloudinary.com/drkelnilg/video/upload/v1739428448/WhatsApp_Video_2025-02-13_at_1.32.42_AM_qxdzmc.mp4',
          caption: 'Viendo mohana  🎥',
        },
        {
          type: 'photo',
          src: 'https://res.cloudinary.com/drkelnilg/image/upload/v1739501481/imagen_2025-02-13_215116071_wwmnkm.png',
          alt: 'Foto 3',
          caption: 'Gracias por el mejor regalo :) siuu',
        },
        {
          type: 'video',
          src: 'https://res.cloudinary.com/drkelnilg/video/upload/v1739428534/WhatsApp_Video_2025-02-13_at_1.32.37_AM_eg5nnr.mp4',
          caption: 'tu patita 🦶🥲',
        }
      ]
    }
  },
  methods: {
    showMessage(message) {
      this.currentMessage = message;
      this.showModal = true;
      setTimeout(() => {
        this.showModal = false;
      }, 3000);
    }
  }
};
</script>

<style scoped>
.valentine-landing {
  font-family: 'Arial', sans-serif;
  text-align: center;
  padding: 20px;
  background: linear-gradient(135deg, #ffffff 0%, #ffffff 100%);
  color: #8b0000;
  min-height: 100vh;
}

/* Header Styles */
header {
  padding: 30px;
  background: linear-gradient(45deg, #d175a3, #14d4ff);
  color: white;
  border-radius: 15px;
  margin-bottom: 30px;
  position: relative;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

.header-animated {
  animation: fadeIn 1s ease-in;
}

.floating-hearts {
  position: absolute;
  font-size: 24px;
  animation: float 3s ease-in-out infinite;
}

.sparkles {
  position: absolute;
  right: 20px;
  top: 20px;
  animation: sparkle 2s ease-in-out infinite;
}

/* Messages Section */
.message-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
  padding: 20px;
}

.message {
  background: white;
  padding: 20px;
  border-radius: 15px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.message:hover {
  transform: translateY(-5px);
}

.bounce-animation {
  animation: bounce 1s ease infinite;
}

/* Photos Section */
.photo-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
  margin-bottom: 30px;
}

.photo-container {
  position: relative;
  cursor: pointer;
  overflow: hidden;
  border-radius: 15px;
  transition: transform 0.3s ease;
}

.photo-container:hover {
  transform: scale(1.05);
}

.photo-container img {
  width: 100%;
  height: 400px;
  object-fit: cover;
  border-radius: 15px;
  transition: filter 0.3s ease;
}

.photo-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
  color: white;
  font-size: 1.2em;
}

.photo-container:hover .photo-overlay {
  opacity: 1;
}


.special-moments {
  margin: 40px 0;
}

.moment-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.moment-image {
  max-width: 100%;
  height: auto;
  border-radius: 15px;
  margin-bottom: 10px;
}

.moment-video {
  max-width: 100%;
  border-radius: 15px;
  margin-bottom: 10px;
}

.moment-caption {
  font-size: 1.2em;
  color: #8b0000;
  margin-top: 10px;
}

.custom-carousel {
  max-width: 80%; /* Ajusta el ancho del carrusel */
  margin: 0 auto; /* Centra el carrusel horizontalmente */
}

.custom-carousel .moment-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.custom-carousel .moment-image,
.custom-carousel .moment-video {
  width: 100%;
  height: auto;
  max-height: 400px; /* Ajusta la altura máxima de los elementos del carrusel */
  object-fit: contain; /* Asegura que el contenido se ajuste sin recortarse */
  border-radius: 15px;
  margin-bottom: 10px;
}

.custom-carousel .moment-caption {
  font-size: 1.2em;
  color: #8b0000;
  margin-top: 10px;
}

/* Modal Styles */
.message-modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
}

.modal-content {
  background: white;
  padding: 20px;
  border-radius: 15px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
  max-width: 80%;
  animation: scaleIn 0.3s ease;
}

/* Footer Styles */
footer {
  padding: 20px;
  background: linear-gradient(45deg, #d175a3, #14d4ff);
  color: white;
  border-radius: 15px;
  margin-top: 30px;
  position: relative;
}

.footer-hearts span {
  animation: pulse 2s infinite;
}

/* Animations */
@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-20px); }
}

@keyframes sparkle {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.5; }
}

@keyframes bounce {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-5px); }
}

@keyframes pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.2); }
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes scaleIn {
  from { transform: scale(0.8); opacity: 0; }
  to { transform: scale(1); opacity: 1; }
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 10px;
  animation: bounce 2s infinite;
}

h2 {
  font-size: 2rem;
  color: #171617;
  margin-bottom: 20px;
  position: relative;
  display: inline-block;
}

h2::after {
  content: '';
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, #1457ff, transparent);
}

.subtitle-animated {
  animation: fadeIn 2s ease;
}

@media (max-width: 768px) {
  .photo-grid {
    grid-template-columns: 1fr;
  }

  .message-container {
    grid-template-columns: 1fr;
  }

  h1 {
    font-size: 2rem;
  }
}

.dedicated-song {
  margin: 40px 0;
  text-align: center;
  background-color: #8ebcb5;
  padding: 20px;
  border-radius: 15px;
}

.dedicated-song h2 {
  font-size: 2rem;
  color: #666666;
  margin-bottom: 20px;
}

.dedicated-song h4,
.dedicated-song p {
  color: #000000;
}

.dedicated-song audio {
  width: 100%;
  max-width: 600px;
  border-radius: 15px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}
</style>
