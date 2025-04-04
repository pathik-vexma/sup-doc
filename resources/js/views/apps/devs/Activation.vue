  <template>
      <div 
        class="activation-page" 
        style="font-family: var(--font-nunito); background-color: var(--color-off-white); color: var(--color-body); padding: 3rem 2rem; margin-left: 110px;"
      >
        <!-- Hero Section with Animation -->
        <header class="activation-header">
          <h1 class="main-heading">Choose Your Plan & Activate Your Account</h1>
          <p class="subtitle">Welcome to our platform! Select one of our flexible subscription plans below.</p>
          <div class="accent-line"></div>
          <div class="hero-image-container">
            <img
              src="@/../../public/images/pricing.webp"
              alt="Activation Banner"
              class="hero-image"
            />
          </div>
        </header>
    
        <!-- Activation Steps With Visual Elements -->
        <section class="activation-steps">
          <h2 class="section-heading">
            <span class="section-icon"><img src="@/../../public/images/rocket.gif" alt="rocket" style="width: 40px; height: 40px;"/></span>
            How Activation Works
          </h2>
          
          <div class="steps-container">
            <div class="steps-grid">
              <div class="step-card" v-for="(step, index) in activationSteps" :key="index">
                <div class="step-number">{{ index + 1 }}</div>
                <div class="step-content">
                  <h3 class="step-title">{{ step.title }}</h3>
                  <p class="step-description">{{ step.description }}</p>
                </div>
              </div>
            </div>
            
            <div class="steps-image-container">
              <img
                src="@/../../public/images/sign-up-account.png"
                alt="Activation Steps"
                class="steps-image"
              />
              <div class="image-overlay">
                <div class="overlay-content">
                  <span class="overlay-icon">💡</span>
                  <p>Once activated, manage everything from a central dashboard!</p>
                </div>
              </div>
            </div>
          </div>
          
          <div class="tip-box">
            <div class="tip-icon">💡</div>
            <div class="tip-content">
              Once your Admin account is active, you can manage everything from a central dashboard.
              Monitor production, track orders, assign tasks to Employees, and offer Customers an easy way to stay updated on their inquiries.
              Our platform ensures smooth collaboration.
            </div>
          </div>
        </section>
    
        <!-- Features Carousel -->
        <section class="features-section">
          <div class="section-divider">
            <span class="divider-line"></span>
            <span class="divider-text">Platform Features</span>
            <span class="divider-line"></span>
          </div>
          
          <div class="carousel-container">
            <div class="carousel-slides">
              <div class="carousel-slide" :class="{ active: currentSlide === 0 }">
                <div class="feature-card">
                  <div class="feature-icon"><img src="@/../../public/images/analytics.gif" alt="analytics" style="width: 64px; height: 64px;"/></div>
                  <h3 class="feature-title">Real-time Analytics</h3>
                  <p class="feature-description">Monitor performance metrics and make data-driven decisions with comprehensive dashboards.</p>
                </div>
              </div>
              <div class="carousel-slide" :class="{ active: currentSlide === 1 }">
                <div class="feature-card">
                  <div class="feature-icon"><img src="@/../../public/images/teamwork.gif" alt="teamwork" style="width: 64px; height: 64px;"/></div>
                  <h3 class="feature-title">Team Collaboration</h3>
                  <p class="feature-description">Connect your entire team with integrated communication and task management tools.</p>
                </div>
              </div>
              <div class="carousel-slide" :class="{ active: currentSlide === 2 }">
                <div class="feature-card">
                  <div class="feature-icon"><img src="@/../../public/images/password.gif" alt="password" style="width: 64px; height: 64px;"/></div>
                  <h3 class="feature-title">Role-based Access</h3>
                  <p class="feature-description">Control who sees what with customizable permission levels for employees and customers.</p>
                </div>
              </div>
              <div class="carousel-slide" :class="{ active: currentSlide === 3 }">
                <div class="feature-card">
                  <div class="feature-icon"><img src="@/../../public/images/companalysis.gif" alt="icon" style="width: 64px; height: 64px;"/></div>
                  <h3 class="feature-title">Comprehensive Part Tracking</h3>
                  <p class="feature-description">Comprehensive Part Tracking delivers real-time visibility and analytics, ensuring every component meets quality, compliance, and efficiency standards.</p>
                </div>
              </div>
              <div class="carousel-slide" :class="{ active: currentSlide === 4 }">
                <div class="feature-card">
                  <div class="feature-icon"><img src="@/../../public/images/teamwork.gif" alt="teamwork" style="width: 64px; height: 64px;"/></div>
                  <h3 class="feature-title">Shop floor Management</h3>
                  <p class="feature-description">Shop Floor Management optimizes production with real-time tracking and streamlined workflows, enhancing overall efficiency.</p>
                </div>
              </div>
              <div class="carousel-slide" :class="{ active: currentSlide === 5 }">
                <div class="feature-card">
                  <div class="feature-icon"><img src="@/../../public/images/teamwork.gif" alt="teamwork" style="width: 64px; height: 64px;"/></div>
                  <h3 class="feature-title">Go Paperless with Digital Job Cards</h3>
                  <p class="feature-description">Go Paperless with Digital Job Cards: Streamline operations by replacing paper with efficient, digital task management.</p>
                </div>
              </div>
              <div class="carousel-slide" :class="{ active: currentSlide === 6 }">
                <div class="feature-card">
                  <div class="feature-icon"><img src="@/../../public/images/teamwork.gif" alt="teamwork" style="width: 64px; height: 64px;"/></div>
                  <h3 class="feature-title">Agile ERP and CRM Tools</h3>
                  <p class="feature-description">Agile ERP and CRM Tools streamline business processes and elevate customer engagement with flexible, integrated solutions.</p>
                </div>
              </div>
            </div>
            
            <div class="carousel-controls">
              <div class="carousel-indicators">
                <span 
                  v-for="(_, index) in 3" 
                  :key="index" 
                  class="indicator-dot" 
                  :class="{ active: currentSlide === index }" 
                  @click="setSlide(index)"
                ></span>
              </div>
              <div class="carousel-arrows">
                <button class="arrow-btn prev-arrow" @click="prevSlide">
                  <span>◀</span>
                </button>
                <button class="arrow-btn next-arrow" @click="nextSlide">
                  <span>▶</span>
                </button>
              </div>
            </div>
          </div>
        </section>
    
        <!-- Enhanced CTA Section -->
        <section class="cta-section">
          <div class="cta-content">
            <h2 class="cta-title">Ready to Get Started?</h2>
            <p class="cta-description">
              Create your Admin account now and take control of your entire workflow.
              Whether you're a small team or a growing enterprise, our platform scales with your business.
            </p>
            <div class="cta-button-container">
              <a href="https://vexmacloud.com/pricing" target="_blank" class="cta-button">
                View Pricing Plans <span class="btn-icon">→</span>
              </a>
            </div>
          </div>
          <div class="cta-animation">
            <div class="pulse-circle"></div>
            <div class="pulse-circle delay-1"></div>
            <div class="pulse-circle delay-2"></div>
          </div>
        </section>
        
        <!-- Testimonials Section -->
        <section class="testimonials-section">
          <div class="section-divider">
            <span class="divider-line"></span>
            <span class="divider-text">What Our Customers Say</span>
            <span class="divider-line"></span>
          </div>
          
          <div class="testimonials-grid">
            <div class="testimonial-card">
              <div class="quote-mark">"</div>
              <p class="testimonial-text">This platform has transformed how we manage our workflow. The employee portal makes task assignment incredibly efficient.</p>
              <div class="testimonial-author">
                <div class="author-avatar">PB</div>
                <div class="author-info">
                  <div class="author-name">Pathik bhatt</div>
                  <div class="author-role">Project Manager</div>
                </div>
              </div>
            </div>
            
            <div class="testimonial-card">
              <div class="quote-mark">"</div>
              <p class="testimonial-text">The customer portal has improved our client satisfaction rates by 40%. They love the transparency and easy access to information.</p>
              <div class="testimonial-author">
                <div class="author-avatar">U</div>
                <div class="author-info">
                  <div class="author-name">Udith</div>
                  <div class="author-role">Customer Success</div>
                </div>
              </div>
            </div>
          </div>
        </section>
      </div>
    </template>
    
    <script lang="ts">
    import { defineComponent, ref, onMounted } from "vue";
    
    export default defineComponent({
      name: "EnhancedActivationPage",
      setup() {
        const activationSteps = ref([
          {
            title: "Select a Plan",
            description: "Pick the subscription that best fits your needs and business requirements."
          },
          {
            title: "Sign Up as Admin",
            description: "Provide your details to create an Admin account and set up your organization."
          },
          {
            title: "Add Employees & Customers",
            description: "Invite team members and customers via email to join your platform."
          },
          {
            title: "Grant Access",
            description: "Employees and Customers each get their own portal for tasks or inquiries."
          },
          {
            title: "Manage & Monitor",
            description: "Enjoy real-time dashboards, streamlined workflows, and easy collaboration."
          }
        ]);
        
        // Carousel logic
        const currentSlide = ref(0);
        const totalSlides = 7;
        
        const nextSlide = () => {
          currentSlide.value = (currentSlide.value + 1) % totalSlides;
        };
        
        const prevSlide = () => {
          currentSlide.value = (currentSlide.value - 1 + totalSlides) % totalSlides;
        };
        
        const setSlide = (index) => {
          currentSlide.value = index;
        };
        
        // Auto-rotate carousel
        let carouselInterval;
        
        onMounted(() => {
          // Initialize carousel auto-rotation
          carouselInterval = setInterval(() => {
            nextSlide();
          }, 5000);
          
          // Clean up interval on component unmount
          return () => {
            clearInterval(carouselInterval);
          };
        });
        
        return {
          activationSteps,
          currentSlide,
          nextSlide,
          prevSlide,
          setSlide
        };
      }
    });
    </script>
    <style scoped>
    :root {
      /* Font Families */
      --font-quicksand: 'Quicksand', sans-serif;
      --font-nunito-sans: 'Nunito Sans', sans-serif;
      --font-nunito: 'Nunito', sans-serif;
    
      /* Colours */
      --color-primary: #2667FF;
      --color-secondary: #0B1460;
      --color-tertiary: #6EF1B2;
      --color-body: #5C6185;
      --color-white: #fafafa;
      --color-black: #000000;
      --color-off-white: #F6F9FB;
      --color-primary-5: rgb(175, 199, 255);
      --color-primary-7: rgba(38, 103, 255, 0.07);
      --color-primary-10: rgba(38, 103, 255, 0.1);
      --color-secondary-10: rgba(11, 20, 96, 0.1);
      --color-white-10: rgba(255, 255, 255, 0.1);
      --color-white-60: rgba(255, 255, 255, 0.6);
      --color-white-70: rgba(255, 255, 255, 0.7);
      --color-dark: #151516;
      --color-deep-dark: #0B0B0B;
    }
    
    /* Main Container */
    .activation-page {
      max-width: 1200px;
      margin: 40px auto;
      margin-top: 20px;
      margin-left: 180px; /* Added margin-left for desktop/PC */
      padding: 30px;
      background: var(--color-off-white);
      border-radius: 16px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
      font-family: var(--font-nunito);
      color: var(--color-body);
    }
    
    /* Header Section */
    .activation-header {
      text-align: center;
      margin-bottom: 60px;
      position: relative;
    }
    
    .main-heading {
      font-family: var(--font-quicksand);
      font-size: 32px;
      color: var(--color-secondary);
      margin: 0 0 10px;
      font-weight: 700;
      animation: fadeInDown 0.8s ease-out;
    }
    
    .subtitle {
      font-size: 18px;
      color: var(--color-body);
      margin-bottom: 15px;
      max-width: 700px;
      margin-left: auto;
      margin-right: auto;
      animation: fadeInUp 0.8s ease-out;
    }
    
    .accent-line {
      height: 4px;
      width: 80px;
      background: linear-gradient(to right, var(--color-primary), var(--color-tertiary));
      margin: 15px auto;
      border-radius: 2px;
      animation: expandWidth 1s ease-out;
    }
    
    .hero-image-container {
      margin-top: 30px;
      border-radius: 16px;
      margin-left: 10px;
      overflow: hidden;
      box-shadow: 0 15px 30px rgba(11, 20, 96, 0.15);
      position: relative;
      animation: fadeInUp 1s ease-out;
      transition: transform 0.5s ease;
    }
    
    .hero-image-container:hover {
      transform: translateY(-5px);
      box-shadow: 0 20px 40px rgba(11, 20, 96, 0.2);
    }
    
    .hero-image {
      width: 100%;
      max-width: 900px;
      display: block;
      margin-left: 50px;
      transition: transform 0.5s ease;
    }
    
    .hero-image-container:hover .hero-image {
      transform: scale(1.02);
    }
    
    /* Activation Steps Section */
    .activation-steps {
      margin: 80px 0;
      position: relative;
    }
    
    .section-heading {
      font-family: var(--font-quicksand);
      font-size: 26px;
      color: var(--color-secondary);
      margin-bottom: 40px;
      font-weight: 600;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    
    .section-icon {
      margin-right: 12px;
      font-size: 28px;
    }
    
    .steps-container {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 40px;
      align-items: center;
    }
    
    .steps-grid {
      display: grid;
      grid-template-columns: 1fr;
      gap: 15px;
    }
    
    .step-card {
      background: white;
      border-radius: 12px;
      padding: 20px;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
      display: flex;
      align-items: flex-start;
      transition: all 0.3s ease;
      cursor: pointer;
    }
    
    .step-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 10px 20px rgba(38, 103, 255, 0.1);
      border-left: 4px solid var(--color-primary);
    }
    
    .step-number {
      display: flex;
      align-items: center;
      justify-content: center;
      width: 40px;
      height: 40px;
      background: var(--color-primary-7);
      color: var(--color-primary);
      border-radius: 50%;
      font-weight: bold;
      font-size: 18px;
      margin-right: 15px;
      flex-shrink: 0;
    }
    
    .step-content {
      flex: 1;
    }
    
    .step-title {
      font-family: var(--font-quicksand);
      font-size: 18px;
      font-weight: 600;
      color: var(--color-secondary);
      margin: 0 0 8px;
    }
    
    .step-description {
      font-size: 15px;
      line-height: 1.5;
      margin: 0;
      color: var(--color-body);
    }
    
    .steps-image-container {
      position: relative;
      border-radius: 16px;
      overflow: hidden;
      box-shadow: 0 15px 30px rgba(11, 20, 96, 0.15);
      transition: all 0.3s ease;
    }
    
    .steps-image-container:hover {
      transform: translateY(-5px);
    }
    
    .steps-image {
      width: 100%;
      display: block;
      transition: transform 0.5s ease;
    }
    
    .steps-image-container:hover .steps-image {
      transform: scale(1.05);
    }
    
    .image-overlay {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      background: linear-gradient(transparent, rgba(11, 20, 96, 0.8));
      padding: 20px;
      transform: translateY(100%);
      transition: transform 0.3s ease;
    }
    
    .steps-image-container:hover .image-overlay {
      transform: translateY(0);
    }
    
    .overlay-content {
      display: flex;
      align-items: center;
      color: white;
    }
    
    .overlay-icon {
      font-size: 22px;
      margin-right: 10px;
    }
    
    .tip-box {
      display: flex;
      background-color: rgba(46, 204, 113, 0.1);
      border-left: 4px solid var(--color-tertiary);
      padding: 20px;
      border-radius: 12px;
      margin-top: 40px;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
    }
    
    .tip-icon {
      font-size: 24px;
      margin-right: 15px;
      flex-shrink: 0;
    }
    
    .tip-content {
      font-size: 16px;
      color: var(--color-body);
      line-height: 1.6;
    }
    
    /* Features Carousel */
    .features-section {
      margin: 80px 0;
    }
    
    .section-divider {
      display: flex;
      align-items: center;
      margin: 30px 0;
    }
    
    .divider-line {
      flex-grow: 1;
      height: 1px;
      background-color: rgba(92, 97, 133, 0.2);
    }
    
    .divider-text {
      padding: 0 20px;
      font-size: 22px;
      font-weight: 600;
      font-family: var(--font-quicksand);
      color: var(--color-secondary);
    }
    
    .carousel-container {
      position: relative;
      padding: 20px 0 60px;
    }
    
    .carousel-slides {
      position: relative;
      min-height: 200px;
    }
    
    .carousel-slide {
      display: none;
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      transition: opacity 0.5s ease-in-out;
      opacity: 0;
    }
    
    .carousel-slide.active {
      display: block;
      opacity: 1;
      animation: fadeIn 0.5s ease-out;
    }
    
    .feature-card {
      background: white;
      border-radius: 16px;
      padding: 30px;
      text-align: center;
      box-shadow: 0 10px 30px rgba(11, 20, 96, 0.1);
      max-width: 800px;
      margin: 0 auto;
      transition: all 0.3s ease;
    }
    
    .feature-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 15px 40px rgba(11, 20, 96, 0.15);
    }
    
    .feature-icon {
      font-size: 40px;
      margin-bottom: 20px;
    }
    
    .feature-title {
      font-family: var(--font-quicksand);
      font-size: 22px;
      color: var(--color-secondary);
      margin-bottom: 15px;
    }
    
    .feature-description {
      font-size: 16px;
      line-height: 1.6;
      color: var(--color-body);
    }
    
    .carousel-controls {
      position: absolute;
      bottom: 10px;
      left: 0;
      right: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    
    .carousel-indicators {
      display: flex;
      justify-content: center;
      margin-bottom: 15px;
    }
    
    .indicator-dot {
      width: 10px;
      height: 10px;
      border-radius: 50%;
      background-color: rgba(38, 103, 255, 0.2);
      margin: 0 5px;
      cursor: pointer;
      transition: all 0.3s ease;
    }
    
    .indicator-dot.active {
      background-color: var(--color-primary);
      transform: scale(1.3);
    }
    
    .carousel-arrows {
      display: flex;
      justify-content: space-between;
      width: 100px;
    }
    
    .arrow-btn {
      width: 36px;
      height: 36px;
      border-radius: 50%;
      background: white;
      border: 1px solid rgba(92, 97, 133, 0.2);
      color: var(--color-body);
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      transition: all 0.3s ease;
    }
    
    .arrow-btn:hover {
      background: var(--color-primary);
      color: white;
      border-color: var(--color-primary);
    }
    
    /* CTA Section */
    .cta-section {
      text-align: center;
      background: linear-gradient(135deg, rgba(38, 103, 255, 0.1), rgba(46, 204, 113, 0.1));
      border-radius: 16px;
      padding: 60px 40px;
      margin-top: 80px;
      position: relative;
      overflow: hidden;
      box-shadow: 0 15px 30px rgba(11, 20, 96, 0.1);
    }
    
    .cta-content {
      position: relative;
      z-index: 2;
      max-width: 700px;
      margin: 0 auto;
    }
    
    .cta-title {
      font-family: var(--font-quicksand);
      font-size: 28px;
      color: var(--color-secondary);
      margin-bottom: 20px;
      animation: fadeInUp 0.8s ease-out;
    }
    
    .cta-description {
      font-size: 18px;
      line-height: 1.6;
      color: var(--color-body);
      margin-bottom: 30px;
      animation: fadeInUp 1s ease-out;
    }
    
    .cta-button-container {
      display: flex;
      justify-content: center;
      gap: 20px;
    }
    
    .cta-button {
      background: linear-gradient(135deg, #3498db, #3498db);
      color: white;
      border-color: black;
      padding: 15px 40px;
      font-size: 18px;
      font-weight: 600;
      border-radius: 30px;
      cursor: pointer;
      transition: all 0.3s ease;
      box-shadow: 0 4px 12px rgba(46, 204, 113, 0.3);
      display: inline-flex;
      align-items: center;
      animation: fadeInUp 1.2s ease-out;
      text-decoration: none;
    }
    
    .btn-icon {
      margin-left: 10px;
      transition: transform 0.3s ease;
    }
    
    .cta-button:hover {
      transform: translateY(-5px);
      box-shadow: 0 12px 30px rgba(38, 103, 255, 0.4);
    }
    
    .cta-button:hover .btn-icon {
      transform: translateX(5px);
    }
    
    .cta-animation {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      z-index: 1;
    }
    
    .pulse-circle {
      position: absolute;
      width: 300px;
      height: 300px;
      border-radius: 50%;
      background: rgba(38, 103, 255, 0.05);
      transform: translate(-50%, -50%);
      animation: pulse 3s infinite;
    }
    
    .delay-1 {
      animation-delay: 1s;
    }
    
    .delay-2 {
      animation-delay: 2s;
    }
    
    /* Testimonials Section */
    .testimonials-section {
      margin: 80px 0 40px;
    }
    
    .testimonials-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 30px;
      margin-top: 40px;
    }
    
    .testimonial-card {
      background: rgba(21, 119, 124, 0.178);
      border-radius: 16px;
      padding: 30px;
      box-shadow: 0 10px 30px rgba(11, 20, 96, 0.08);
      position: relative;
      transition: all 0.3s ease;
    }
    
    .testimonial-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 15px 40px rgba(11, 20, 96, 0.12);
    }
    
    .quote-mark {
      position: absolute;
      top: 40px;
      left: 20px;
      font-size: 80px;
      line-height: 0;
      color: rgba(0, 17, 80, 0.498);
      font-family: Georgia, serif;
    }
    
    .testimonial-text {
      font-size: 16px;
      line-height: 1.7;
      color: var(--color-body);
      margin: 0 0 20px;
      position: relative;
      z-index: 1;
      padding-top: 10px;
    }
    
    .testimonial-author {
      display: flex;
      align-items: center;
    }
    
    .author-avatar {
      width: 50px;
      height: 50px;
      border-radius: 50%;
      background: var(--color-primary);
      color: rgb(12, 8, 37);
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: bold;
      margin-right: 15px;
    }
    
    .author-name {
      font-weight: 600;
      color: var(--color-secondary);
      font-size: 16px;
    }
    
    .author-role {
      font-size: 14px;
      color: var(--color-body);
    }
    
    /* Animations */
    @keyframes fadeInDown {
      from {
        opacity: 0;
        transform: translateY(-20px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
    
    @keyframes fadeInUp {
      from {
        opacity: 0;
        transform: translateY(20px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
    
    @keyframes fadeIn {
      from {
        opacity: 0;
      }
      to {
        opacity: 1;
      }
    }
    
    @keyframes expandWidth {
      from {
        width: 0;
      }
      to {
        width: 80px;
      }
    }
    
    @keyframes pulse {
      0% {
        transform: translate(-50%, -50%) scale(0.8);
        opacity: 0.8;
      }
      50% {
        transform: translate(-50%, -50%) scale(1.2);
        opacity: 0;
      }
      100% {
        transform: translate(-50%, -50%) scale(0.8);
        opacity: 0;
      }
    }
    
    /* Responsive Styles */
    @media (max-width: 1200px) {
      .activation-page {
        margin-left: auto; /* Reset the left margin on smaller screens */
        margin-right: auto;
        padding: 20px;
        width: 90%; /* Added to ensure it takes most of the screen width */
      }
      
      .hero-image {
        margin-left: 0; /* Reset the left margin on smaller screens */
        max-width: 100%; /* Ensure image is responsive */
      }
    }
    
    @media (max-width: 992px) {
      .activation-page {
        width: 95%; /* Further increase width on smaller screens */
      }
      
      .steps-container {
        grid-template-columns: 1fr;
        gap: 40px;
      }
      
      .steps-image-container {
        order: -1;
      }
      
      .testimonials-grid {
        grid-template-columns: 1fr;
      }
      
      .cta-button-container {
        flex-direction: column;
        align-items: center;
      }
    }
    
    @media (max-width: 768px) {
      .activation-page {
        width: 100%; /* Full width on mobile */
        margin: 10px auto; /* Reduced margin */
        padding: 15px; /* Reduced padding */
      }
      
      .main-heading {
        font-size: 26px;
      }
      
      .subtitle {
        font-size: 16px;
      }
      
      .section-heading {
        font-size: 22px;
      }
      
      .step-title {
        font-size: 16px;
      }
      
      .step-description {
        font-size: 14px;
      }
      
      .cta-section {
        padding: 40px 20px;
      }
      
      .cta-title {
        font-size: 24px;
      }
      
      .cta-description {
        font-size: 16px;
      }
      
      .cta-button {
        padding: 12px 30px;
        font-size: 16px;
      }
    }
  </style>