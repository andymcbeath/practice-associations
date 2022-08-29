<template>
  <nav
    class="navbar sticky-top navbar-expand-sm navbar-dark"
    style="background-color: blue"
  >
    <div class="container-fluid">
      <a class="navbar-brand" href="#">
        <img
          src="./assets/noteImage.png"
          alt=""
          width="30"
          height="30"
          class="d-inline-block align-text-top"
        />
        Noted
      </a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="/">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="/signup"
              >Sign Up</a
            >
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/scores">All Scores</a>
          </li>
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="/login"
              >Log In</a
            >
          </li>
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="/logout"
              >Log Out</a
            >
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <!-- <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/signup">Signup</router-link> |
    <router-link to="/login">Login</router-link> |
    <router-link to="/logout">Logout</router-link> |
    <router-link to="/scores">All Scores</router-link> |
    <router-link to="/scores/new">New Score</router-link>
  </nav>
  <router-view /> -->
  <router-view />
</template>

<style>
body {
  background: whitesmoke;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: whitesmoke;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
