<template onload="sidepanel()">
  <main>
    <header>
      <div id="wrapper">
        <div class="overlay"></div>

        <!-- Sidebar -->
        <nav
          class="navbar navbar-inverse fixed-top"
          id="sidebar-wrapper"
          role="navigation"
        >
          <ul class="sidebar-nav">
            <div class="sidebar-header">
              <div class="sidebar-brand">
                <a href="#">
                  <img
                    src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/5b/Insert_image_here.svg/1024px-Insert_image_here.svg.png"
                    alt="VHLogo"
                    width="150px"
                  />
                </a>
              </div>
            </div>
            <li><Link href="/"><i class="fas fa-home icons-menu"></i>Início </Link></li>
            <li class="dropdown">
              <a href="" class="dropdown-toggle" data-toggle="dropdown"
                ><i class="fas fa-users icons-menu"></i>Usuários</a
              >
              <ul class="dropdown-menu animated fadeInLeft" role="menu">
                <!--<div class="dropdown-header">Ferramentas</div>-->
                <li><Link href="#/usuario/cadastro"><i class="fas fa-user-plus icons-menu"></i>Cadastrar</Link></li>
                <li><Link href="#/usuario/lista"><i class="fas fa-search icons-menu"></i>Pesquisar</Link></li>
              </ul>
            </li>

            <li class="dropdown">
              <a href="" class="dropdown-toggle" data-toggle="dropdown"
                ><i class="fas fa-building icons-menu"></i>Departamento</a
              >
              <ul class="dropdown-menu animated fadeInLeft" role="menu">
                <!--<div class="dropdown-header">Ferramentas</div>-->
                <li><Link href="#/departamento/cadastro"><i class="fas fa-user-plus icons-menu"></i>Cadastrar</Link></li>
                <li><Link href="#/departamentos/lista"><i class="fas fa-search icons-menu"></i>Pesquisar</Link></li>
              </ul>
            </li>
           
            <li class="dropdown">
              <a href="" class="dropdown-toggle" data-toggle="dropdown"
                ><i class="fas fa-wrench icons-menu"></i>Cargos</a
              >
              <ul class="dropdown-menu animated fadeInLeft" role="menu">
                <!--<div class="dropdown-header">Ferramentas</div>-->
                <li><Link href="#/cargo/cadastro"><i class="fas fa-user-plus icons-menu"></i>Cadastrar</Link></li>
                <li><Link href="#/cargos/lista"><i class="fas fa-search icons-menu"></i>Pesquisar</Link></li>
              </ul>
            </li>

            <li><Link href="#/sobre"><i class="fas fa-info-circle icons-menu"></i>Sobre</Link></li>            
            <li>
              <Link href="#/logout"><i class="fas fa-sign-out-alt icons-menu"></i>Sair</Link>
            </li>
          </ul>
        </nav>

        <!-- /#sidebar-wrapper -->

        <!-- Page Content -->
        <div id="page-content-wrapper">
          <button
            type="button"
            class="hamburger animated fadeInLeft is-closed"
            data-toggle="offcanvas"
          >
            <span class="hamb-top"></span>
            <span class="hamb-middle"></span>
            <span class="hamb-bottom"></span>
          </button>
          <div class="container">
            <article>
              <slot />
            </article>
          </div>
        </div>
        <!-- /#page-content-wrapper -->
      </div>
      <!-- /#wrapper -->
    </header>
  </main>
</template>

<script>
import { Link } from "@inertiajs/inertia-vue";
export default {
  components: {
    Link,
  },
  mounted() {
    $(function () {
      var trigger = $(".hamburger"),
        overlay = $(".overlay"),
        isClosed = false;
      trigger.click(function () {
        hamburger_cross();
      });
      function hamburger_cross() {
        if (isClosed == true) {
          overlay.hide();
          trigger.removeClass("is-open");
          trigger.addClass("is-closed");
          isClosed = false;
        } else {
          overlay.show();
          trigger.removeClass("is-closed");
          trigger.addClass("is-open");
          isClosed = true;
        }
      }
      $('[data-toggle="offcanvas"]').click(function () {
        $("#wrapper").toggleClass("toggled");
      });
    });
  }
  
};
</script>