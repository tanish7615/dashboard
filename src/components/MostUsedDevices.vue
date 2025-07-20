<template>
  <div class="card h-100 border-0 shadow-sm">
    <div class="card-header bg-white border-0 d-flex justify-content-between align-items-center">
      <h6 class="fw-bold mb-0">Today Used Devices</h6>
      <button class="btn btn-sm btn-outline-light text-muted border-0">
        <i class="bi bi-three-dots"></i>
      </button>
    </div>
    <div class="card-body position-relative">
      <!-- Circular Progress Chart -->
      <div class="d-flex justify-content-center mb-3">
        <div class="position-relative" style="width: 120px; height: 120px;">
          <canvas ref="deviceChart" width="120" height="120"></canvas>
          <div class="position-absolute top-50 start-50 translate-middle text-center">
            <div class="fw-bold fs-4">100</div>
            <small class="text-muted">Overall</small>
          </div>
        </div>
      </div>

      <!-- Device List -->
      <div class="device-list">
        <div class="d-flex justify-content-between align-items-center mb-2">
          <div class="d-flex align-items-center">
            <span class="badge bg-primary rounded-pill me-2" style="width: 8px; height: 8px;"></span>
            <small>Macbook</small>
          </div>
          <small class="fw-bold">80</small>
        </div>
        <div class="d-flex justify-content-between align-items-center mb-2">
          <div class="d-flex align-items-center">
            <span class="badge bg-warning rounded-pill me-2" style="width: 8px; height: 8px;"></span>
            <small>Keyboard</small>
          </div>
          <small class="fw-bold">13</small>
        </div>
        <div class="d-flex justify-content-between align-items-center">
          <div class="d-flex align-items-center">
            <span class="badge bg-success rounded-pill me-2" style="width: 8px; height: 8px;"></span>
            <small>Headphones</small>
          </div>
          <small class="fw-bold">07</small>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MostUsedDevices',
  mounted() {
    this.drawChart()
  },
  methods: {
    drawChart() {
      const canvas = this.$refs.deviceChart
      const ctx = canvas.getContext('2d')
      const centerX = canvas.width / 2
      const centerY = canvas.height / 2
      const radius = 45

      // Clear canvas
      ctx.clearRect(0, 0, canvas.width, canvas.height)

      // Draw background circle
      ctx.beginPath()
      ctx.arc(centerX, centerY, radius, 0, 2 * Math.PI)
      ctx.strokeStyle = '#e9ecef'
      ctx.lineWidth = 8
      ctx.stroke()

      // Draw progress arcs
      const data = [
        { value: 80, color: '#6c5ce7', startAngle: -Math.PI / 2 },
        { value: 13, color: '#fdcb6e', startAngle: 0 },
        { value: 7, color: '#00b894', startAngle: Math.PI / 3 }
      ]

      let currentAngle = -Math.PI / 2
      data.forEach((item, index) => {
        const percentage = item.value / 100
        const endAngle = currentAngle + (2 * Math.PI * percentage)

        ctx.beginPath()
        ctx.arc(centerX, centerY, radius, currentAngle, endAngle)
        ctx.strokeStyle = item.color
        ctx.lineWidth = 8
        ctx.lineCap = 'round'
        ctx.stroke()

        currentAngle = endAngle
      })
    }
  }
}
</script>

<style scoped>
.card {
  transition: all 0.3s ease;
}

.card:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 15px rgba(0,0,0,0.1) !important;
}

.badge.rounded-pill {
  padding: 0;
  border-radius: 50% !important;
}
</style>