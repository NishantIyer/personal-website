
<template>
  <div class="container">
    <header class="header">
      <nav class="nav desktop-nav">
        <div class="left">
          <router-link to="/" title="Home" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil:home-alt"></i>
            </span>
            <span class="nav-text">Home</span>
          </router-link>
        </div>
        <div class="center">
          <router-link to="/posts" title="Blog" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil:file-edit-alt"></i>
            </span>
            <span class="nav-text">Blog</span>
          </router-link>
          <router-link to="/academia" title="Academia" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil:book-open"></i>
            </span>
            <span class="nav-text">Academia</span>
          </router-link>
          <router-link to="/projects" title="Projects" class="nav-link">
            <span class="nav-icon">
              <i class="i-material-symbols-code-blocks"></i>
            </span>
            <span class="nav-text">Projects</span>
          </router-link>
        </div>
        <div class="right">
          <a href="https://github.com/NishantIyer" target="_blank" title="GitHub" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil-github-alt"></i>
            </span>
            <span class="nav-text">GitHub</span>
          </a>
          <a href="https://nishantiyer.netlify.app/pics" target="_blank" title="Pictures" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil:picture"></i>
            </span>
            <span class="nav-text"></span>
          </a>
        </div>
      </nav>
      <nav class="nav mobile-nav">
        <div class="mobile-nav-row">
          <router-link to="/" title="Home" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil:home-alt"></i>
            </span>
          </router-link>
          <router-link to="/posts" title="Blog" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil:file-edit-alt"></i>
            </span>
            <span class="nav-text">Blog</span>
          </router-link>
          <router-link to="/academia" title="Academia" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil:book-open"></i>
            </span>
            <span class="nav-text"></span>
          </router-link>
          <router-link to="/projects" title="Projects" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil:web-grid"></i>
            </span>
            <span class="nav-text"></span>
          </router-link>
          <a href="https://github.com/NishantIyer" target="_blank" title="GitHub" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil-github-alt"></i>
            </span>
          </a>
          <a href="https://nishantiyer.netlify.app/pics" target="_blank" title="Pictures" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil:picture"></i>
            </span>
          </a>
        </div>
        <div class="mobile-nav-row">
          <router-link to="/posts" title="Blog" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil:file-edit-alt"></i>
            </span>
            <span class="nav-text">Blog</span>
          </router-link>
          <router-link to="/academia" title="Academia" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil:book-open"></i>
            </span>
            <span class="nav-text"></span>
          </router-link>
          <router-link to="/projects" title="Projects" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil:web-grid"></i>
            </span>
            <span class="nav-text"></span>
          </router-link>
        </div>
      </nav>
    </header>
  </div>
</template>

<style scoped>
.container {
  max-width: 100%;
  overflow-x: hidden;
}

.header {
  position: relative;
}

.nav {
  padding: 0.5rem;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 0.9rem;
}

.desktop-nav {
  background-color: transparent;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 999;
}

.left {
  display: flex;
  align-items: center;
}

.center {
  display: flex;
  align-items: center;
}

.right {
  display: flex;
  align-items: center;
}

.nav-link {
  text-decoration: none;
  color: #fff;
  font-weight: bold;
  padding: 0.5rem;
  margin: 0 0.2rem;
  position: relative;
}

.nav-link:hover::before {
  content: "";
  position: absolute;
  bottom: -0.5rem;
  left: 0;
  right: 0;
  height: 0.2rem;
  background-color: #fff;
  border-radius: 0.2rem;
}

.mobile-nav {
  background-color: transparent;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 999;
  display: none;
  flex-direction: column;
}

.mobile-nav-row {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
}

.nav-icon {
  display: inline-block;
  font-size: 1rem;
  margin-right: 0.2rem;
}

.nav-text {
  display: inline-block;
  margin-right: 0.2rem;
}

@media screen and (max-width: 767px) {
  .desktop-nav {
    display: none;
  }
  .mobile-nav {
    display: flex;
  }
}
</style>

<script>
function toTop() {
  window.scrollTo({
    top: 0,
    behavior: 'smooth',
  })
}

const { y: scroll } = useWindowScroll()

export default {
  name: "Header",
  data() {
    return {
      isMobileNavOpen: false,
    };
  },
};
</script>
