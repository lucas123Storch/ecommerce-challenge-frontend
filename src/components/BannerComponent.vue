<template>
  <div>
    <transition-group name="fade" tag="div">
      <div v-for="i in [currentIndex]" :key="i">
        <img :src="currentImg" />
      </div>
    </transition-group>
    <a class="prev" @click="prev" href="#">&#10094; Anterior</a>
    <a class="next" @click="next" href="#">&#10095; Próximo</a>
  </div>
</template>

<script>
export default {
  data() {
    return {
      images: [
        "https://firebasestorage.googleapis.com/v0/b/deploy-test-34131.appspot.com/o/banner1.png?alt=media&token=69737be9-30bf-4cac-a6d1-46c3abfc58ae",
        "https://firebasestorage.googleapis.com/v0/b/deploy-test-34131.appspot.com/o/banner2.png?alt=media&token=1fd271cd-126b-470d-b2ff-1314a310ba3f",
        "https://firebasestorage.googleapis.com/v0/b/deploy-test-34131.appspot.com/o/banner3.png?alt=media&token=e5a99270-39a9-4e16-b37d-164db8f286ed"
      ],
      timer: null,
      currentIndex: 0
    };
  },
  methods: {
    next: function() {
      this.currentIndex += 1;
    },
    prev: function() {
      this.currentIndex -= 1;
    }
  },
  computed: {
    currentImg: function() {
      return this.images[Math.abs(this.currentIndex) % this.images.length];
    }
  }
}
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: all 0.9s ease;
  overflow: hidden;
  visibility: visible;
  position: absolute;
  width:100%;
  opacity: 1;
}

.fade-enter,
.fade-leave-to {
  visibility: hidden;
  width:100%;
  opacity: 0;
}

img {
  height:600px;
  width:100%
}

.prev, .next {
  cursor: pointer;
  position: absolute;
  top: 40%;
  width: auto;
  padding: 16px;
  color: white;
  font-weight: bold;
  font-size: 18px;
  transition: 0.7s ease;
  border-radius: 0 4px 4px 0;
  text-decoration: none;
  user-select: none;
}

.next {
  right: 0;
}

.prev {
  left: 0;
}

.prev:hover, .next:hover {
  background-color: rgba(0,0,0,0.9);
}
</style>