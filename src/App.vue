<template>
  <div class="vue-tempalte">
    <!-- Navigation -->
    <nav
      class="navbar shadow rounded justify-content-between flex-nowrap flex-row fixed-top"
    >
      <div  class="container">
        <a
          class="navbar-brand float-left"
          href="/"
          target="_blank"
        >
          <span style="color:coral;font-weight:700;font-size:2rem">Tech</span>.io
        </a>
        <ul class="nav navbar-nav flex-row float-right">
          <li class="nav-item">
            <router-link class="navbutton btn btn-light" to="/">Sign in</router-link>
          </li>
          <li class="nav-item">
            <router-link class="navbutton btn btn-outline-light" to="/signup"
              >Sign up</router-link
            >
          </li>
        </ul>
      </div>
    </nav>

    <!-- Main -->
    <div class="App">
          <div class="overflow"></div>

      <div class="vertical-center">
        <div class="inner-block">
          <router-view />
        </div>
      </div>
    </div>
  </div>
</template>
