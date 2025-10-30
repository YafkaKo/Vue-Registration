<script setup lang="ts">
import SliderItem from "~/components/slider/SliderItem.vue";
import LionImg from "~/assets/images/Lion_waiting_in_Namibia.jpg";
import CherepahaImg from "~/assets/images/0ac1a26ca0da7817c0b2a2992720bfba.jpg";
import OrelImg from "~/assets/images/5cf3b023-f2fe-53ce-a9ca-e57ebdacabb8.jpg";
import PandaImg from "~/assets/images/ef8de9d9e2b36b660fc9c7698d91f6c7.jpg";
import KitImg from "~/assets/images/i.jpg";
export interface Animal {
  id: number;
  name: string;
  image: string;
  description: string;
}

const animals: Animal[] = [
  {
    id: 0,
    name: "Африканский лев",
    image: LionImg,
    description:
      "Крупный хищник из семейства кошачьих. Царь зверей, обитающий в саваннах Африки. Самцы отличаются гривой и крупными размерами.",
  },
  {
    id: 1,
    name: "Большая панда",
    image: PandaImg,
    description:
      "Медведь, питающийся в основном бамбуком. Обитает в горных регионах Китая. Символ Всемирного фонда дикой природы.",
  },
  {
    id: 2,
    name: "Орлан-белохвост",
    image: OrelImg,
    description:
      "Крупная хищная птица семейства ястребиных. Обитает near водоемов, питается рыбой и водоплавающими птицами.",
  },
  {
    id: 3,
    name: "Морская черепаха",
    image: CherepahaImg,
    description:
      "Крупная рептилия, проводящая большую часть жизни в морской воде. Мигрирует на тысячи километров для размножения.",
  },
  {
    id: 4,
    name: "Синий кит",
    image: KitImg,
    description:
      "Крупнейшее животное на Земле. Длина достигает 33 метров, вес - 150 тонн. Питается крилем и мелкими ракообразными.",
  },
];

let autoPlayInterval: number | null = null
const currentAnimal = ref(0);
const isAnimating = ref(false)
const isDragging = ref(false)
const dragStartX = ref(0)
const dragOffset = ref(0)

const getSlideStyle = (index: number) => {
  const diff = index - currentAnimal.value
  const totalSlides = animals.length

  let normalizedDiff = diff
  if (Math.abs(diff) > totalSlides / 2) {
    normalizedDiff = diff > 0 ? diff - totalSlides : diff + totalSlides
  }

  const styles: any = {
    transform: '',
    zIndex: '',
    opacity: ''
  }

  switch (normalizedDiff) {
    case -2:
      styles.transform = 'translateX(-280px) scale(0.8)'
      styles.zIndex = 1
      styles.opacity = '0.7'
      break
    case -1:
      styles.transform = 'translateX(-140px) scale(0.9)'
      styles.zIndex = 2
      styles.opacity = '0.8'
      break
    case 0:
      styles.transform = 'translateX(0) scale(1)'
      styles.zIndex = 3
      styles.opacity = '1'
      break
    case 1:
      styles.transform = 'translateX(140px) scale(0.9)'
      styles.zIndex = 2
      styles.opacity = '0.8'
      break
    case 2:
      styles.transform = 'translateX(280px) scale(0.8)'
      styles.zIndex = 1
      styles.opacity = '0.7'
      break
    default:
      styles.transform = 'translateX(0) scale(0.6)'
      styles.zIndex = 0
      styles.opacity = '0'
  }

  return styles
}
const goToSlide = (index: number) => {
  if (isAnimating.value || index === currentAnimal.value) return

  isAnimating.value = true
  currentAnimal.value = index

  setTimeout(() => {
    isAnimating.value = false
  }, 600)
}

const findNextIndex = ():number =>{
    if((currentAnimal.value + 1) < animals.length){return currentAnimal.value + 1}
    else return 0
}
const findPrevIndex = ():number =>{
    if((currentAnimal.value - 1) > -1){return currentAnimal.value - 1}
    else return animals.length - 1
}

const next = () => {
  const nextIndex = findNextIndex()
  goToSlide(nextIndex)
}
const prev = () => {
  const prevIndex = findPrevIndex()
  goToSlide(prevIndex)
}

const handleKeydown = (event: KeyboardEvent) => {
  if (event.key === 'ArrowLeft') prev()
  if (event.key === 'ArrowRight') next()
}
const startAutoPlay = () => {
  return setInterval(() => {
    if(!isDragging.value){
    next()
    }

  }, 5000)
}
const startDrag = (event:MouseEvent) =>{
  isDragging.value = true
  dragOffset.value = 0

  dragStartX.value = event.clientX
  document.addEventListener('mousemove', handleDragMove)
  document.addEventListener('mouseup', endDrag)
}

const handleDragMove = (event:MouseEvent)=>{
  if(!isDragging.value) return
  event.preventDefault()

  const deltaX = event.clientX - dragStartX.value
  const maxDrag = 300
  dragOffset.value = Math.max(-maxDrag,Math.min(maxDrag,deltaX))
}

const endDrag = () =>{
  if(!isDragging.value) return

  isDragging.value = false
  const dragStrong = 50
  const dragDistance = Math.abs(dragOffset.value)

  if(dragDistance > dragStrong){
    if(dragOffset.value > 0){
      prev()
    } else{
      next()
    }
  }
  dragOffset.value = 0

  document.removeEventListener('mousemove', handleDragMove)
  document.removeEventListener('mouseup', endDrag)
}
onMounted(() => {
  document.addEventListener('keydown', handleKeydown)
  autoPlayInterval = startAutoPlay()
})

onUnmounted(() => {
  document.removeEventListener('keydown', handleKeydown)
  if (autoPlayInterval) {
    clearInterval(autoPlayInterval)
  }
})
</script>

<template>
  <div class="slider-container" @mousedown="startDrag">
    <div class="slider-top"  >
      <SliderItem
        v-for="(animal, index) in animals"
        :current-animal="currentAnimal"
        :animal="animal"
        @click.prevent="goToSlide(index)"
        :isDragging="isDragging"
        :drag-offset="currentAnimal === index ? dragOffset : 0"
        :slide-style="getSlideStyle(index)"
      />
    </div>
    <div class="slider-pagination">
      <button
        v-for="(animal,index) in animals"
        @click.prevent="goToSlide(index)"
        :class="
          currentAnimal === animal.id
            ? 'slider-pagination-item active'
            : 'slider-pagination-item'
        "
      ></button>
    </div>
  </div>
</template>

<style lang="scss">
.slider {
  &-container {

    background-color: #fff;
    border-radius: 16px;
    padding: 24px 12px;
    position: relative;
    width: 100%;
    max-width: 1200px;
    height: 500px;
    overflow: hidden;
  }
  &-top {
    width: 100%;
    height: 100%;
    perspective: 800px;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
    transform-style: preserve-3d;
  }
  &-pagination {
    position: absolute;
    bottom: 40px;
    display: flex;
    gap: 16px;
    left: calc(50% - 60px);
  }
  &-pagination-item {
    width: 18px;
    height: 18px;
    border-radius: 50%;
    background-color: gray;
    transition: all 0.3s ease;
  }
  &-pagination-item.active {
    background-color: lightgray;
  }
}
</style>
