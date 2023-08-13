<template>
  <div class="background">
    <canvas ref="el" :width="size.width" :height="size.height" />
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, reactive, computed } from 'vue'
import { useWindowSize } from '@vueuse/core'

const el = ref<HTMLCanvasElement | null>(null)
const size = reactive(useWindowSize())

let dots: Dot[] = []
const interactiveRadius = 50
const interactiveRadiusSquared = interactiveRadius * interactiveRadius

interface Dot {
  x: number
  y: number
  radius: number
  color: string
  dx: number
  dy: number
  originalRadius: number
}

function createDot(): Dot {
  const x = Math.random() * size.width
  const y = Math.random() * size.height
  const radius = Math.random() * 3 + 1
  const originalRadius = radius
  const color = getRandomColor()
  const dx = (Math.random() - 0.5) * 2
  const dy = (Math.random() - 0.5) * 2

  return { x, y, radius, color, dx, dy, originalRadius }
}

function getRandomColor(): string {
  const colors = ['#37306B','#66347F','#9E4784','#D27685']
  const index = Math.floor(Math.random() * colors.length)
  return colors[index]
}

function updateDots(): void {
  dots.forEach((dot) => {
    dot.x += dot.dx
    dot.y += dot.dy

    if (dot.x + dot.radius > size.width || dot.x - dot.radius < 0) {
      dot.dx = -dot.dx
    }

    if (dot.y + dot.radius > size.height || dot.y - dot.radius < 0) {
      dot.dy = -dot.dy
    }
  })
}

function drawDots(ctx: CanvasRenderingContext2D): void {
  ctx.clearRect(0, 0, size.width, size.height)
  dots.forEach((dot) => {
    ctx.beginPath()
    ctx.arc(dot.x, dot.y, dot.radius, 0, Math.PI * 2)
    ctx.shadowColor = dot.color
    ctx.shadowBlur = dot.radius * 2
    ctx.fillStyle = dot.color
    ctx.fill()
  })
}

function handleMouseMove(event: MouseEvent): void {
  const mouseX = event.pageX
  const mouseY = event.pageY

  dots.forEach((dot) => {
    const distanceSquared = (mouseX - dot.x) ** 2 + (mouseY - dot.y) ** 2
    if (distanceSquared < interactiveRadiusSquared && dot.radius < dot.originalRadius * 2) {
      dot.radius += 0.5
      disruptDot(dot)
    } else if (dot.radius > dot.originalRadius) {
      dot.radius -= 0.5
    }
  })
}

function handleTouchMove(event: TouchEvent): void {
  const touch = event.touches[0]
  const touchX = touch.pageX
  const touchY = touch.pageY

  dots.forEach((dot) => {
    const distanceSquared = (touchX - dot.x) ** 2 + (touchY - dot.y) ** 2
    if (distanceSquared < interactiveRadiusSquared && dot.radius < dot.originalRadius * 2) {
      dot.radius += 0.5
      disruptDot(dot)
    } else if (dot.radius > dot.originalRadius) {
      dot.radius -= 0.5
    }
  })
}

function disruptDot(dot: Dot): void {
  dot.dx = (Math.random() - 0.5) * 2
  dot.dy = (Math.random() - 0.5) * 2
}

onMounted(() => {
  const canvas = el.value!
  const ctx = canvas.getContext('2d')!
  canvas.width = size.width
  canvas.height = size.height

  for (let i = 0; i < 50; i++) {
    dots.push(createDot())
  }

  const animation = () => {
    updateDots()
    drawDots(ctx)
    requestAnimationFrame(animation)
  }

  animation()

  window.addEventListener('mousemove', handleMouseMove)
  window.addEventListener('touchmove', handleTouchMove, { passive: true })
})

const mask = computed(() => 'radial-gradient(circle, transparent, black);')
</script>

<style scoped>
.background {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: -1;
  pointer-events: none;
  background-color: #000000;
}

canvas {
  position: fixed;
  top: 0;
  left: 0;
}
</style>
