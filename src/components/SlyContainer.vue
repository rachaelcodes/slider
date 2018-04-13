<template>
    <div class="sl-container">
        <div class="sl-view">
            <div ref="transition" class="sl-slide">
                    <!-- <component v-bind:is="views[viewIndex]"/> -->
                    <!-- <div v-for="view in views" :key="view"> -->
                        <sly-view v-for="(view, index) in views" :key="view" :num="view" v-if="index===viewIndex"/>
                    <!-- </div> -->
            </div>
        </div>
        <div class="sl-nav">
            <button class='sl-btn' id="sl-left" v-on:click="this.moveLeft">
                <img src="../assets/left-arrow.png" alt="toggle left">
            </button>
            <button class='sl-btn' v-for="(view, index) in views" :key="view" v-on:click="updateIndex(index)">
                <img src="../assets/empty-circle.png" alt="tab" v-if="index!=viewIndex">
                <img src="../assets/filled-circle.png" alt="tab" v-if="index===viewIndex">
                </button>
            <button class='sl-btn' id="sl-right" v-on:click="this.moveRight">
                <img src="../assets/right-arrow.png" alt="toggle right">
            </button>
        </div>
    </div>
</template>

<script>
import SlyView from './SlyView'

export default {
  data: function () {
      return {
          viewIndex: 0,
          views: ['one', 'two', 'three']
      }
  },
  components: {
      'sly-view': SlyView,
    //   'one': {template: '<div class="sl-element one" ></div>'},
    //   'two': {template: '<div class="sl-element two" ></div>'},
    //   'three': {template: '<div class="sl-element three" ></div>'}
  },
  methods: {
      moveRight: function () {

        this.$refs.transition.classList.remove('slide-in-right')
        this.$refs.transition.classList.remove('slide-in-left')
          
          this.$refs.transition.classList.add('slide-out-right')
          setTimeout(()=> { 
              if (this.viewIndex===2) {this.viewIndex = 0}
                else {this.viewIndex++}

                this.$refs.transition.classList.add('slide-in-left')
                this.$refs.transition.classList.remove('slide-out-right')
          }, 250)
          
      },
      moveLeft: function () {
        this.$refs.transition.classList.remove('slide-in-right')
        this.$refs.transition.classList.remove('slide-in-left')
          
        this.$refs.transition.classList.add('slide-out-left')
        setTimeout(()=> { 
            if (this.viewIndex===0) {this.viewIndex = 2}
            else {this.viewIndex--}

                this.$refs.transition.classList.add('slide-in-right')
                this.$refs.transition.classList.remove('slide-out-left')
          }, 250)


          
      },
      updateIndex: function (number) {
        this.$refs.transition.classList.remove('slide-in-right')
        this.$refs.transition.classList.remove('slide-in-left')

        if (this.viewIndex > number) {
          this.$refs.transition.classList.add('slide-out-left')
            setTimeout(()=> { 
            this.viewIndex = number

                this.$refs.transition.classList.add('slide-in-right')
                this.$refs.transition.classList.remove('slide-out-left')
          }, 250)
        } else if (this.viewIndex < number ) {
          
        this.$refs.transition.classList.add('slide-out-right')
          setTimeout(()=> { 
              this.viewIndex = number

              this.$refs.transition.classList.add('slide-in-left')
              this.$refs.transition.classList.remove('slide-out-right')
          }, 250)
        
      }
      }
  }
}
</script>

<style>
.sl-container{
    height: 500px;
    width: 500px;
    padding: 50px;
    margin: auto;
    background-color: palevioletred
}

.sl-view {
    margin: auto;
    height: 400px;
    width: 400px;

    overflow: hidden;
}

.sl-slide {
    height: 400px;
    width: 400px;
}

.sl-element {
    height: 400px;
    width: 400px;
}

.sl-btn {
    border:none;
    background-color: palevioletred;
}

.sl-nav {
    padding-top: 15px;
}

.one {
    background-image: url('../assets/packshot-parrot-petite-en-GB.jpg')
}

.two {
    background-image: url('../assets/packshot-butterfly-petite-en-GB.jpg')
}

.three {
    background-image: url('../assets/packshot-jellyfish-petite-en-GB.jpg')
}

.slide-out-left {
    animation-duration: .3s;
    animation-name: slide-out-left;
    animation-timing-function: ease-in;
}
.slide-out-right {
    animation-duration: .3s;
    animation-name: slide-out-right;
    animation-timing-function: ease-in;
}
.slide-in-left {
    animation-duration: .3s;
    animation-name: slide-in-left;
    animation-timing-function: ease-out;
}
.slide-in-right {
    animation-duration: .3s;
    animation-name: slide-in-right;
    animation-timing-function: ease-out;
}

@keyframes slide-out-left {
    from {
    transform: translateX(0);
    opacity: 1;
  }

  to {
    transform: translateX(-400px);
    opacity: 0;
  }
}

@keyframes slide-out-right {
    from {
    transform: translateX(0);
    opacity: 1;
  }

  to {
    transform: translateX(400px);
    opacity: 0;
  }
}

@keyframes slide-in-left {
    from {
    transform: translateX(-400px);
    opacity: 0;
  }
    
    to {
    transform: translateX(0);
    opacity: 1;
  }

  
}

@keyframes slide-in-right {
    from {
    transform: translateX(400px);
    opacity: 0;
  }
    
    to {
    transform: translateX(0);
    opacity: 1;
  }

  
}


</style>


