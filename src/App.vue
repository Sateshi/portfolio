<script setup lang="ts">
import { onMounted, ref } from 'vue'

// Portfolio data - because everything starts with good variable names
const name = "Johan Bergmans"
const title = "Full Stack Developer"
const subtitle = "// TODO: Change the world, one commit at a time"
const prompt = "dev@localhost:~$"
const vimMode = ":wq"

// Mobile menu state
const isMobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}

// Scroll animation setup
onMounted(() => {
  const observerOptions = {
    threshold: 0.1,
    rootMargin: '0px 0px -50px 0px'
  }

  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('in-view')
      }
    })
  }, observerOptions)

  // Observe all scroll-animate elements
  document.querySelectorAll('.scroll-animate').forEach(el => {
    observer.observe(el)
  })

  // Enhanced smooth scrolling for anchor links
  document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function (e) {
      e.preventDefault()
      const target = document.querySelector(this.getAttribute('href'))
      if (target) {
        target.scrollIntoView({
          behavior: 'smooth',
          block: 'start'
        })
      }
    })
  })
})
</script>

<template>
  <div class="min-h-screen bg-gradient-to-br from-gray-900 via-slate-800 to-black text-white font-mono">
    <!-- Hero Section -->
    <header id="hero" class="relative min-h-screen flex items-center justify-center px-4 sm:px-6 lg:px-8 xl:px-12">
      <!-- Background Pattern -->
      <div class="absolute inset-0 overflow-hidden">
        <div class="absolute top-1/4 left-1/4 w-48 h-48 sm:w-72 sm:h-72 lg:w-96 lg:h-96 bg-green-500 rounded-full opacity-8 blur-3xl"></div>
        <div class="absolute bottom-1/4 right-1/4 w-40 h-40 sm:w-60 sm:h-60 lg:w-80 lg:h-80 bg-slate-600 rounded-full opacity-12 blur-3xl"></div>
        <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-[300px] h-[300px] sm:w-[450px] sm:h-[450px] lg:w-[600px] lg:h-[600px] bg-gradient-to-r from-gray-700 to-slate-800 rounded-full opacity-8 blur-3xl"></div>
      </div>
      
      <!-- Main Content -->
      <div class="relative z-10 text-center max-w-xs sm:max-w-2xl lg:max-w-4xl xl:max-w-6xl mx-auto">
        <!-- Terminal Prompt -->
        <div class="text-left mb-6 sm:mb-8 text-green-400 text-xs sm:text-sm md:text-base hero-animate" style="animation-delay: 0.1s;">
          <span class="text-gray-400">{{ prompt }}</span> whoami
        </div>
        
        <!-- Name -->
        <h1 class="text-3xl sm:text-4xl md:text-6xl lg:text-7xl xl:text-8xl font-bold tracking-tight text-white mb-3 sm:mb-4 font-mono hero-animate" style="animation-delay: 0.3s;">
          <span class="block text-green-400 hover:animate-pulse transition-all duration-300">&gt;</span>
          <span class="block hover:text-green-400 transition-colors duration-300">{{ name.split(' ')[0].toLowerCase() }}</span>
          <span class="block text-blue-400 hover:text-blue-300 transition-colors duration-300">{{ name.split(' ')[1]?.toLowerCase() || '' }}</span>
        </h1>
        
        <!-- Title with cursor -->
        <div class="text-sm sm:text-lg md:text-xl lg:text-2xl xl:text-3xl text-gray-300 mb-6 sm:mb-8 font-mono hero-animate" style="animation-delay: 0.5s;">
          <span class="text-gray-500">const </span> 
          <span class="text-blue-400 hover:text-blue-300 transition-colors duration-300">role</span> 
          <span class="text-gray-500"> = </span> 
          <span class="text-green-300 hover:text-green-200 transition-colors duration-300">"{{ title }}"</span>
          <span class="animate-pulse text-white">|</span>
        </div>
        
        <!-- Subtitle as comment -->
        <p class="text-sm sm:text-base md:text-lg lg:text-xl xl:text-2xl leading-relaxed text-gray-400 max-w-xs sm:max-w-lg md:max-w-2xl lg:max-w-3xl mx-auto mb-8 sm:mb-12 font-mono hero-animate hover:text-gray-300 transition-colors duration-300" style="animation-delay: 0.7s;">
          {{ subtitle }}
        </p>
        
        <!-- Code block style info -->
        <div class="text-left max-w-xs sm:max-w-lg md:max-w-xl lg:max-w-2xl mx-auto mb-8 sm:mb-12 bg-black/30 border border-gray-700 rounded p-3 sm:p-4 text-xs sm:text-sm font-mono hover-lift hover-glow hero-animate" style="animation-delay: 0.9s;">
          <div class="terminal-line text-gray-500 mb-1 sm:mb-2">// Current status:</div>
          <div class="terminal-line text-green-400">✓ Coffee level: Maximum</div>
          <div class="terminal-line text-green-400">✓ Dark theme: Obviously</div>
          <div class="terminal-line text-yellow-400">⚠ Sleep schedule: undefined</div>
        </div>
        
        <!-- Terminal Commands -->
        <div class="flex flex-col sm:flex-row gap-3 sm:gap-4 justify-center items-center font-mono hero-animate" style="animation-delay: 1.1s;">
          <a href="#work" class="group px-4 sm:px-6 py-2 sm:py-3 bg-green-600 text-black font-bold hover:brightness-110 transition-all duration-150 border border-green-600 text-sm sm:text-base w-full sm:w-auto text-center">
            <span>./view_projects.sh</span>
          </a>
          <a href="#contact" class="px-4 sm:px-6 py-2 sm:py-3 border border-blue-500 text-blue-400 font-bold hover:text-blue-300 transition-colors duration-150 text-sm sm:text-base w-full sm:w-auto text-center">
            <span>git contact</span>
          </a>
        </div>
      </div>
      
      <!-- Scroll Indicator -->
      <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2">
        <div class="flex flex-col items-center text-gray-400 font-mono">
          <span class="text-xs mb-2">{{ vimMode }}</span>
          <div class="w-px h-12 bg-gray-500 animate-pulse"></div>
        </div>
      </div>
    </header>

    <!-- Navigation (Fixed) -->
    <nav class="fixed top-0 left-0 right-0 z-50 bg-black/80 backdrop-blur-sm border-b border-green-500/30 font-mono">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 xl:px-12">
        <div class="flex justify-between items-center h-14 sm:h-16">
          <!-- Terminal-style Logo -->
          <a href="#hero" class="text-base sm:text-lg font-bold text-green-400 hover:text-green-300 transition-colors duration-150" @click="closeMobileMenu">
            <span class="text-gray-500">~/</span>{{ name.split(' ').map(n => n[0].toLowerCase()).join('') }}
          </a>
          
          <!-- Desktop Menu -->
          <div class="hidden sm:flex space-x-4 md:space-x-6 lg:space-x-8">
            <a href="#work" class="text-xs sm:text-sm font-bold text-gray-300 hover:text-green-400 transition-all duration-300 hover:scale-110 transform">ls projects/</a>
            <a href="#about" class="text-xs sm:text-sm font-bold text-gray-300 hover:text-green-400 transition-all duration-300 hover:scale-110 transform">cat about.md</a>
            <a href="#contact" class="text-xs sm:text-sm font-bold text-gray-300 hover:text-green-400 transition-all duration-300 hover:scale-110 transform">ping me</a>
          </div>
          
          <!-- Mobile Menu Button -->
          <button @click="toggleMobileMenu" class="sm:hidden text-gray-300 hover:text-green-400 font-bold transition-colors duration-150">
            <span class="text-xs">{{ isMobileMenuOpen ? 'close' : 'menu' }}</span>
          </button>
        </div>
        
        <!-- Mobile Menu -->
        <div v-show="isMobileMenuOpen" class="sm:hidden border-t border-gray-700 bg-black/90 backdrop-blur-sm">
          <div class="px-2 pt-2 pb-3 space-y-1">
            <a href="#work" @click="closeMobileMenu" class="block px-3 py-2 text-sm font-bold text-gray-300 hover:text-green-400 hover:bg-gray-800/50 rounded transition-all duration-150">
              <span class="text-green-400">$</span> ls projects/
            </a>
            <a href="#about" @click="closeMobileMenu" class="block px-3 py-2 text-sm font-bold text-gray-300 hover:text-green-400 hover:bg-gray-800/50 rounded transition-all duration-150">
              <span class="text-green-400">$</span> cat about.md
            </a>
            <a href="#contact" @click="closeMobileMenu" class="block px-3 py-2 text-sm font-bold text-gray-300 hover:text-green-400 hover:bg-gray-800/50 rounded transition-all duration-150">
              <span class="text-green-400">$</span> ping me
            </a>
          </div>
        </div>
      </div>
    </nav>

    <!-- Main Content Sections (Placeholder) -->
    <main class="relative z-10">
      <!-- Work Section -->
      <section id="work" class="py-16 sm:py-20 lg:py-24 px-4 sm:px-6 lg:px-8 xl:px-12">
        <div class="max-w-xs sm:max-w-2xl md:max-w-4xl lg:max-w-6xl xl:max-w-7xl mx-auto">
          <!-- Terminal header -->
          <div class="mb-8 sm:mb-10 lg:mb-12 font-mono scroll-animate">
            <div class="text-green-400 mb-3 sm:mb-4 hover:text-green-300 transition-colors duration-300 text-xs sm:text-sm md:text-base">
              <span class="text-gray-400">{{ prompt }}</span> ls projects/ --detailed
            </div>
            <div class="bg-black/30 border border-gray-700 rounded p-4 sm:p-5 lg:p-6 hover-lift hover-glow">
              <div class="text-gray-500 mb-3 sm:mb-4 text-xs sm:text-sm">// Found 42 repositories. Showing featured:</div>
              <h2 class="text-2xl sm:text-3xl md:text-4xl lg:text-5xl xl:text-6xl font-bold text-white mb-6 sm:mb-8">
                <span class="text-green-400 hover:animate-pulse">></span> Featured <span class="text-blue-400 hover:text-blue-300 transition-colors duration-300">Projects</span>
              </h2>
              <p class="text-sm sm:text-base md:text-lg text-gray-300 leading-relaxed hover:text-gray-200 transition-colors duration-300">
                <span class="text-gray-500">/*</span><br>
                &nbsp;&nbsp;Projects built with ❤️, lots of ☕, and probably too much Stack Overflow.<br>
                &nbsp;&nbsp;Each one taught me something new (usually what NOT to do).<br>
                <span class="text-gray-500">*/</span>
              </p>
            </div>
          </div>
        </div>
      </section>
      
      <!-- About Section -->
      <section id="about" class="py-16 sm:py-20 lg:py-24 px-4 sm:px-6 lg:px-8 xl:px-12">
        <div class="max-w-xs sm:max-w-2xl md:max-w-3xl lg:max-w-4xl xl:max-w-5xl mx-auto">
          <!-- Terminal header -->
          <div class="mb-8 sm:mb-10 lg:mb-12 font-mono scroll-animate">
            <div class="text-green-400 mb-3 sm:mb-4 hover:text-green-300 transition-colors duration-300 text-xs sm:text-sm md:text-base">
              <span class="text-gray-400">{{ prompt }}</span> cat about.md
            </div>
            <div class="bg-black/30 border border-gray-700 rounded p-4 sm:p-5 lg:p-6 hover-lift hover-glow">
              <h2 class="text-2xl sm:text-3xl md:text-4xl lg:text-5xl xl:text-6xl font-bold text-white mb-6 sm:mb-8">
                <span class="text-green-400 hover:animate-pulse">#</span> About <span class="text-blue-400 hover:text-blue-300 transition-colors duration-300">Me</span>
              </h2>
              <div class="text-gray-300 leading-relaxed space-y-3 sm:space-y-4">
                <p class="hover:text-gray-200 transition-colors duration-300 text-xs sm:text-sm md:text-base lg:text-lg">
                  <span class="text-yellow-400 hover:text-yellow-300 transition-colors duration-300">const</span> <span class="text-blue-400 hover:text-blue-300 transition-colors duration-300">developer</span> = {<br>
                  &nbsp;&nbsp;<span class="text-green-300 hover:text-green-200 transition-colors duration-300">passion</span>: <span class="text-orange-400 hover:text-orange-300 transition-colors duration-300">"Solving problems with code"</span>,<br>
                  &nbsp;&nbsp;<span class="text-green-300 hover:text-green-200 transition-colors duration-300">editor</span>: <span class="text-orange-400 hover:text-orange-300 transition-colors duration-300">"VSCode"</span>,<br>
                  &nbsp;&nbsp;<span class="text-green-300 hover:text-green-200 transition-colors duration-300">os</span>: <span class="text-orange-400 hover:text-orange-300 transition-colors duration-300">"Windows, MacOS,Linux (btw I use Arch)"</span>,<br>
                  &nbsp;&nbsp;<span class="text-green-300 hover:text-green-200 transition-colors duration-300">languages</span>: [<span class="text-orange-400 hover:text-orange-300 transition-colors duration-300">"JavaScript", "TypeScript", "PHP"</span>],<br>
                  &nbsp;&nbsp;<span class="text-green-300 hover:text-green-200 transition-colors duration-300">motto</span>: <span class="text-orange-400 hover:text-orange-300 transition-colors duration-300">"Code is poetry, bugs are typos"</span><br>
                  };
                </p>
                <p class="text-gray-400 hover:text-gray-300 transition-colors duration-300 text-xs sm:text-sm md:text-base">
                  // I don't just write code, I live it. Started with "Hello World" and never looked back.<br>
                </p>
              </div>
            </div>
          </div>
        </div>
      </section>
      
      <!-- Contact Section -->
      <section id="contact" class="py-16 sm:py-20 lg:py-24 px-4 sm:px-6 lg:px-8 xl:px-12">
        <div class="max-w-xs sm:max-w-2xl md:max-w-3xl lg:max-w-4xl xl:max-w-5xl mx-auto">
          <!-- Terminal header -->
          <div class="mb-8 sm:mb-10 lg:mb-12 font-mono scroll-animate">
            <div class="text-green-400 mb-3 sm:mb-4 hover:text-green-300 transition-colors duration-300 text-xs sm:text-sm md:text-base">
              <span class="text-gray-400">{{ prompt }}</span> ping me --message="Let's build something awesome"
            </div>
            <div class="bg-black/30 border border-gray-700 rounded p-4 sm:p-5 lg:p-6 text-center hover-lift hover-glow">
              <h2 class="text-2xl sm:text-3xl md:text-4xl lg:text-5xl xl:text-6xl font-bold text-white mb-6 sm:mb-8">
                <span class="text-green-400 hover:animate-pulse">></span> Let's <span class="text-blue-400 hover:text-blue-300 transition-colors duration-300">Collaborate</span>
              </h2>
              <p class="text-sm sm:text-base md:text-lg text-gray-300 mb-6 sm:mb-8 hover:text-gray-200 transition-colors duration-300">
                <span class="text-gray-500">// Got a cool project? Just want to talk tech?</span><br>
                <span class="text-green-400 hover:text-green-300 transition-colors duration-300">console.log</span>(<span class="text-orange-400 hover:text-orange-300 transition-colors duration-300">"I'm always up for a good coding challenge!"</span>);
              </p>
              <a href="mailto:bergmans.johan0@gmail.com" class="inline-block px-4 sm:px-6 py-2 sm:py-3 bg-green-600 text-black font-bold hover:brightness-110 transition-all duration-150 font-mono border border-green-600 text-sm sm:text-base">
                <span>./send_email.sh</span>
              </a>
            </div>
          </div>
        </div>
      </section>
    </main>

    <!-- Footer -->
    <footer class="py-8 sm:py-10 lg:py-12 px-4 sm:px-6 lg:px-8 xl:px-12">
      <div class="max-w-xs sm:max-w-2xl md:max-w-4xl lg:max-w-6xl xl:max-w-7xl mx-auto text-center font-mono">
        <div class="text-green-400 mb-2 text-xs sm:text-sm">
          <span class="text-gray-400">{{ prompt }}</span> echo "Thanks for visiting!"
        </div>
        <p class="text-xs sm:text-sm text-gray-400">
          <span class="text-gray-500">//</span> © 2025 {{ name }}. Built with 🖤.
        </p>
        <p class="text-xs text-gray-500 mt-1 sm:mt-2">
          exit 0
        </p>
      </div>
    </footer>
  </div>
</template>

<style scoped>
/* Custom letter spacing utility */
.letter-spacing-wide {
  letter-spacing: 0.2em;
}

/* Smooth scrolling */
html {
  scroll-behavior: smooth;
}

/* Scroll offset for fixed navigation */
section {
  scroll-margin-top: 60px;
}

@media (min-width: 640px) {
  section {
    scroll-margin-top: 80px;
  }
}

/* Custom animations */
@keyframes float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-10px); }
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideInLeft {
  from {
    opacity: 0;
    transform: translateX(-30px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes slideInRight {
  from {
    opacity: 0;
    transform: translateX(30px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes glow {
  0%, 100% { box-shadow: 0 0 5px rgba(34, 197, 94, 0.3); }
  50% { box-shadow: 0 0 20px rgba(34, 197, 94, 0.6), 0 0 30px rgba(34, 197, 94, 0.4); }
}

@keyframes typewriter {
  from { width: 0; }
  to { width: 100%; }
}

.animate-float {
  animation: float 3s ease-in-out infinite;
}

.hero-animate {
  opacity: 0;
  transform: translateY(20px);
  animation: fadeInUp 0.8s ease-out forwards;
}

.animate-fade-in-up {
  animation: fadeInUp 0.8s ease-out forwards;
}

.animate-slide-in-left {
  animation: slideInLeft 0.8s ease-out forwards;
}

.animate-slide-in-right {
  animation: slideInRight 0.8s ease-out forwards;
}

.animate-glow {
  animation: glow 2s ease-in-out infinite;
}

.animate-typewriter {
  overflow: hidden;
  white-space: nowrap;
  animation: typewriter 2s steps(40, end);
}

/* Scroll-triggered animations */
.scroll-animate {
  opacity: 0;
  transform: translateY(30px);
  transition: all 0.8s ease-out;
}

.scroll-animate.in-view {
  opacity: 1;
  transform: translateY(0);
}

/* Hover effects */
.hover-lift {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.hover-lift:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
}

.hover-glow {
  transition: all 0.3s ease;
}

.hover-glow:hover {
  box-shadow: 0 0 15px rgba(34, 197, 94, 0.4);
  border-color: rgb(34, 197, 94);
}

.terminal-line {
  opacity: 0;
  animation: fadeInUp 0.4s ease-out forwards;
}

.hero-animate .terminal-line:nth-child(1) { animation-delay: 1.0s; }
.hero-animate .terminal-line:nth-child(2) { animation-delay: 1.1s; }
.hero-animate .terminal-line:nth-child(3) { animation-delay: 1.2s; }
.hero-animate .terminal-line:nth-child(4) { animation-delay: 1.3s; }
</style>
