<template>
  <div class="onboarding-container">
    <header class="header-section">
      <h1 class="main-heading">How to create an Invoice</h1>
      <div class="progress-container">
        <div class="progress-bar" :style="progressStyle"></div>
      </div>
    </header>
    
    <div class="content-wrapper">
      <!-- Left Side: Carousel with Controls -->
      <div class="carousel-section">
        <transition name="fade">
          <div class="carousel-arrow prev" @click="prevSlide" :class="{ disabled: currentStep === 0 }">
            &#8249;
          </div>
        </transition>
        
        <div class="image-carousel">
          <div 
            class="zoom-wrapper" 
            ref="zoomWrapper" 
            :class="{ 'zoomed': isZoomed }"
            @click="toggleZoom"
            @mousemove="handleZoom"
          >
            <div class="zoom-controls">
              <button class="zoom-button" @click.stop="toggleZoom">
                {{ isZoomed ? '−' : '+' }}
              </button>
            </div>
            <transition name="slide-fade" mode="out-in">
              <img
                :key="currentStep"
                :src="steps[currentStep].image"
                :alt="steps[currentStep].title"
                class="slide-image"
                ref="zoomImage"
              />
            </transition>
          </div>
          
          <div class="carousel-dots">
            <transition-group name="dot-scale">
              <span 
                v-for="(step, index) in steps" 
                :key="index"
                class="carousel-dot" 
                :class="{ active: currentStep === index }"
                @click="goToStep(index)"
              ></span>
            </transition-group>
          </div>
        </div>
        
        <div class="content-section">
          <transition name="fade-slide" mode="out-in">
            <div class="step-info" :key="currentStep">
              <div class="step-header">
                <div class="step-badge">Step {{ currentStep + 1 }}/{{ steps.length }}</div>
                <h2 class="step-title">{{ steps[currentStep].title }}</h2>
              </div>
              
              <div class="step-details">
                <transition-group name="list" tag="ul" class="feature-list">
                  <li v-for="(item, index) in steps[currentStep].details" :key="item">
                    <span class="checkmark">
                      <transition name="check-pop">
                        <span class="check-icon" v-show="showChecks">✓</span>
                      </transition>
                    </span>
                    <span>{{ item }}</span>
                  </li>
                </transition-group>
              </div>
              
              <transition name="bounce">
                <div class="tip-box">
                  <div class="tip-icon pulse">💡</div>
                  <div class="tip-content">{{ steps[currentStep].tip }}</div>
                </div>
              </transition>
            </div>
          </transition>
        </div>
        
        <transition name="fade">
          <div class="carousel-arrow next" @click="nextSlide" :class="{ disabled: currentStep === steps.length - 1 }">
            &#8250;
          </div>
        </transition>
      </div>
    </div>
    
    <!-- Video Tutorial Section -->
    <div class="video-section" ref="videoSection" v-intersect="handleVideoIntersect">
      <h2 class="video-title">Watch Video Tutorial</h2>
      <transition name="reveal">
        <div class="video-container" v-if="videoVisible">
          <iframe
            src="https://www.youtube.com/embed/cq0yA4tQEx0?autoplay=0&controls=1"
            frameborder="0"
            allowfullscreen
            class="video-frame"
          ></iframe>
        </div>
      </transition>
    </div>
    
    <!-- Scroll to top button -->
    <transition name="fade-up">
      <button class="scroll-top-button" @click="scrollToTop" v-show="showScrollButton">
        <span class="top-arrow">↑</span>
      </button>
    </transition>
  </div>
</template>

<script>
import { defineComponent, ref, computed, onMounted, onUnmounted, nextTick } from "vue";
import "@/assets/style.css";

export default defineComponent({
  name: "InvoiceGuide",
  directives: {
    intersect: {
      mounted(el, binding) {
        const observer = new IntersectionObserver(
          ([entry]) => {
            if (entry.isIntersecting) {
              binding.value(true);
            } else {
              binding.value(false);
            }
          },
          {
            threshold: 0.2
          }
        );
        observer.observe(el);
        el._intersectionObserver = observer;
      },
      unmounted(el) {
        if (el._intersectionObserver) {
          el._intersectionObserver.disconnect();
        }
      }
    }
  },
  setup() {
    const steps = ref([
      {
        title: "Generate Invoice from Order Details",
        image: "/images/invoice1.webp",
        details: [
          "Admins or designated employees access the invoice creation module from the order details.",
          "The system automatically pre-fills the invoice with essential order information.",
          "This ensures that the invoice data is accurate and consistent with the order details.",
          "Initiating invoice creation at this stage streamlines the billing process and minimizes manual errors."
        ],
        tip: "Double-check the pre-filled details and use search or filter functions to verify that you are working with the correct order."
      },
      {
        title: "Complete Invoice Details & Notify Customer",
        image: "/images/invoice2.webp",
        details: [
          "Users fill in all mandatory fields in the invoice form, including pricing, taxes, and payment terms.",
          "They carefully review and verify the invoice details for accuracy.",
          "Once finalized, the system confirms the invoice creation.",
          "An automated email and in-app push notification are sent to the customer, ensuring timely communication and transparency."
        ],
        tip: "Be as detailed as possible when entering invoice information and review the form before submission to prevent discrepancies."
      }
    ]);

    const currentStep = ref(0);
    const showScrollButton = ref(false);
    const zoomWrapper = ref(null);
    const zoomImage = ref(null);
    const isZoomed = ref(false);
    const zoomPosition = ref({ x: 50, y: 50 });
    const showChecks = ref(false);
    const videoVisible = ref(false);

    const progressStyle = computed(() => {
      return {
        width: `${(currentStep.value / (steps.value.length - 1)) * 100}%`
      };
    });

    const nextSlide = () => {
      if (currentStep.value < steps.value.length - 1) {
        currentStep.value++;
        isZoomed.value = false;
        showChecks.value = false;
        setTimeout(() => {
          showChecks.value = true;
        }, 500);
      }
    };

    const prevSlide = () => {
      if (currentStep.value > 0) {
        currentStep.value--;
        isZoomed.value = false;
        showChecks.value = false;
        setTimeout(() => {
          showChecks.value = true;
        }, 500);
      }
    };

    const goToStep = (index) => {
      if (index !== currentStep.value) {
        currentStep.value = index;
        isZoomed.value = false;
        showChecks.value = false;
        setTimeout(() => {
          showChecks.value = true;
        }, 500);
      }
    };

    const toggleZoom = () => {
      isZoomed.value = !isZoomed.value;
      
      if (isZoomed.value && zoomWrapper.value && zoomImage.value) {
        updateZoomPosition(zoomPosition.value.x, zoomPosition.value.y);
      }
    };

    const updateZoomPosition = (x, y) => {
      if (zoomImage.value) {
        zoomImage.value.style.transformOrigin = `${x}% ${y}%`;
      }
    };

    const handleZoom = (e) => {
      if (!isZoomed.value || !zoomWrapper.value || !zoomImage.value) return;
      
      const rect = zoomWrapper.value.getBoundingClientRect();
      const x = ((e.clientX - rect.left) / rect.width) * 100;
      const y = ((e.clientY - rect.top) / rect.height) * 100;
      
      zoomPosition.value = { x, y };
      updateZoomPosition(x, y);
    };

    const scrollToTop = () => {
      window.scrollTo({
        top: 0,
        behavior: 'smooth'
      });
    };

    const checkScroll = () => {
      showScrollButton.value = window.pageYOffset > 300;
    };

    const handleVideoIntersect = (isVisible) => {
      if (isVisible) {
        videoVisible.value = true;
      }
    };

    onMounted(() => {
      window.addEventListener('scroll', checkScroll);
      
      // Show check marks with delay on initial load
      setTimeout(() => {
        showChecks.value = true;
      }, 500);
    });

    onUnmounted(() => {
      window.removeEventListener('scroll', checkScroll);
    });

    return {
      steps,
      currentStep,
      showScrollButton,
      zoomWrapper,
      zoomImage,
      isZoomed,
      showChecks,
      videoVisible,
      progressStyle,
      nextSlide,
      prevSlide,
      goToStep,
      toggleZoom,
      handleZoom,
      scrollToTop,
      handleVideoIntersect
    };
  }
});
</script>

