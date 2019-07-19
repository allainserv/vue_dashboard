<template>
  <div id="app">
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-navbar-brand href="#">NavBar</b-navbar-brand>
    
      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item href="#">Link</b-nav-item>
          <b-nav-item href="#" disabled>Disabled</b-nav-item>
        </b-navbar-nav>

        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto">
          <b-nav-form>
            <b-form-input size="sm" class="mr-sm-2" placeholder="Search"></b-form-input>
            <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
          </b-nav-form>

          <b-nav-item-dropdown text="Lang" right>
            <b-dropdown-item href="#">EN</b-dropdown-item>
            <b-dropdown-item href="#">ES</b-dropdown-item>
            <b-dropdown-item href="#">RU</b-dropdown-item>
            <b-dropdown-item href="#">FA</b-dropdown-item>
          </b-nav-item-dropdown>

          <b-nav-item-dropdown right>
            <!-- Using 'button-content' slot -->
            <template slot="button-content"><em>User</em></template>
            <b-dropdown-item href="#">Profile</b-dropdown-item>
            <b-dropdown-item href="#">Sign Out</b-dropdown-item>
          </b-nav-item-dropdown>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <div class="content sidebar-open">
        <div class="sidebar">
        </div>

        <div class="content-body">          
          <b-container>
            <router-view/>
          </b-container>

          <div class="footer">
            
          </div>
        </div>
    </div> 
  </div>
</template>

<style lang="scss">
// Sidebar
$sidebar-width: 300px;
$sidebar-bg: #2f353a;
$sidebar-anim-speed: 0.2s;

// Header
$header-height: 60px;

// Footer 
$footer-height: 30px;
$footer-bg: #000;

html, body {
  height: 100%;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
}

.content {
  height: calc(100% - #{$header-height});
  position: relative;

  .sidebar {
    height: calc(100%);
    position: absolute;
    width: $sidebar-width;
    background: $sidebar-bg;
  }

  .content-body {
    height: 100%;
    width: 100%;
    margin: 0;
    
    .container {
      height: calc( 100% - #{$footer-height});
    }

    .footer {
      height: $footer-height;
      background: $footer-bg;
      display: block;
    }
  }

  &.sidebar-open {
    .sidebar {
      left: 0;
      transition: left $sidebar-anim-speed linear;
    }

    .content-body {
      margin-left: 300px;
      transition: all $sidebar-anim-speed linear;
      width: calc( 100% -  #{$sidebar-width} );
    }
  }

  &.sidebar-closed {
    .sidebar {
      left: $sidebar-width * -1;
      transition: left $sidebar-anim-speed linear;
    }

    .content-body {
      margin-left: 0;
      transition: all $sidebar-anim-speed linear;
      width: 100%;
    }
  }
}

nav {
  padding: 30px;
  height: $header-height;
  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
