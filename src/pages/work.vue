<template>
<Layout :sidebar="true" :footer="true" class="container">



  <header class="uk-section  uk-section-secondary uk-position-relative">
    <div class="uk-container uk-container-small uk-text-center">
      <h1 class="uk-margin-top">Our Works</h1>
      <p class="uk-text-large">This is a text that describes the album, its creator.</p>
      <!-- arrow bottom -->
      <div class="uk-position-z-index uk-text-center uk-position-bottom">
        <a href="#main" data-uk-scroll="duration: 500" data-uk-icon="icon: arrow-down; ratio: 2" class="uk-margin-bottom"></a>
      </div>

    </div>

  </header>
  <!--/HERO-->
  <!-- CONTENT -->
  <main id="main" class="uk-section uk-section-muted uk-padding-remove-top">
    <div class="uk-container">


      <nav class="uk-section-muted uk-margin-bottom">
        <div class="uk-container uk-padding-small">
          <ul class="uk-breadcrumb">
            <li>
              <g-link to="/">Home</g-link>
            </li>
            <li class="uk-disabled"><a>Work</a></li>






          </ul>
        </div>
      </nav>


      <section style="display:none;">
      <button
         v-bind:class="{ 'i-am-active': button_active_state }"
         v-on:click="button_active_state = !button_active_state"
         name="button"
       >START
     </button>


      <button v-bind:class="{ 'i-am-active': button_active_state }" id="3">3</button>

   </section>
   
      <div class="uk-grid uk-grid-medium uk-child-width-1-2 uk-child-width-1-2@m uk-child-width-1-3@l uk-grid-match"

      v-bind:class="{ 'i-am-active': button_active_state }"

      data-uk-lightbox="toggle:a.uk-position-cover" data-uk-grid="masonry: true">
        <!-- item -->
        <ul class="uk-inline" v-for="edge in $page.posts.edges" :key="edge.node.id" style="list-style-type: none;">
          <li>
            <g-link :to="edge.node.path" class=" uk-link-reset" title="View Project">
              <div class="uk-card uk-card-default uk-card-small">
                <g-image class="uk-position-top uk-position-z-index" quality="100" fit="contain" src="~/assets/images/browser-top.png" />
                <div class="uk-card-media-top">
                  <div class="uk-inline-clip uk-transition-toggle uk-light">
                    <g-image style="padding-top:7px;" quality="100" :src="edge.node.image" fit="contain" :alt="edge.node.title" />
                    <div class="uk-transition-fade uk-position-cover uk-overlay uk-overlay-primary uk-flex uk-flex-center uk-flex-middle">
                      <div data-uk-margin class="uk-transition-slide-bottom-small">
                        <span data-uk-icon="icon: plus; ratio: 1.3"></span>
                      </div>
                    </div>
                  </div>
                </div>
                <header class="uk-card-header">
                  <div class="uk-grid-small uk-flex uk-flex-middle" data-uk-grid>
                    <div class="uk-width-expand">
                      <button class="uk-button uk-button-text" style="font-size:16px;line-height:1">{{ edge.node.title }}</button>
                      <p class="uk-text-meta uk-margin-small"><time datetime="2016-04-01T19:00">{{ edge.node.date }}</time></p>
                    </div>
                  </div>
                </header>
              </div>
            </g-link>
          </li>
        </ul>
      </div>
    </div>
  </main>
  <!-- /CONTENT -->




  <!--/FOOTER-->
  <!-- OFFCANVAS -->
  <div id="offcanvas-nav" data-uk-offcanvas="flip: true; overlay: true">
    <div class="uk-offcanvas-bar uk-offcanvas-bar-animation uk-offcanvas-slide">
      <button class="uk-offcanvas-close uk-close uk-icon" type="button" data-uk-close></button>
      <ul class="uk-nav uk-nav-default">
        <li class="uk-active"><a href="#">Active</a></li>
        <li class="uk-parent">
          <a href="#">Parent</a>
          <ul class="uk-nav-sub">
            <li><a href="#">Sub item</a></li>
            <li><a href="#">Sub item</a></li>
          </ul>
        </li>
        <li class="uk-nav-header">Header</li>
        <li><a href="#js-options"><span class="uk-margin-small-right uk-icon" data-uk-icon="icon: table"></span> Item</a></li>
        <li><a href="#"><span class="uk-margin-small-right uk-icon" data-uk-icon="icon: thumbnails"></span> Item</a></li>
        <li class="uk-nav-divider"></li>
        <li><a href="#"><span class="uk-margin-small-right uk-icon" data-uk-icon="icon: trash"></span> Item</a></li>
      </ul>
      <h3>Title</h3>
      <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
    </div>
  </div>
  <!-- /OFFCANVAS -->
  <!-- MODALS -->
  <div id="modal-center" class="uk-flex-top" data-uk-modal>
    <div class="uk-modal-dialog uk-modal-body uk-margin-auto-vertical">
      <button class="uk-modal-close-default" type="button" data-uk-close></button>
      <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute
        irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
    </div>
  </div>

  <div id="modal-media-vimeo" class="uk-flex-top" data-uk-modal>
    <div class="uk-modal-dialog uk-width-auto uk-margin-auto-vertical">
      <button class="uk-modal-close-outside" type="button" data-uk-close></button>
      <iframe src="//player.vimeo.com/video/87816089" width="500" height="281" data-uk-video></iframe>
    </div>
  </div>
  <!-- /MODALS -->

</Layout>
</template>




<page-query>
  {
    posts: allPost {
      edges {
        node {
          title
          date (format: "MMMM YYYY")
          description
          image
          path
        }
      }
    }
  }
</page-query>


<static-query>
query {
  metaData {
    siteName
  }
}
</static-query>


<script>


export default {
  data: function () {
    return {
      button_active_state: false
    }
  },
  components: {

  },
  metaInfo: {
    title: 'Works'
  }
}
</script>

<style>
time:hover{
  text-decoration: none;
}

.i-am-active {
  color: orange;
  background: red;
}

</style>
