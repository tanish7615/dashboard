<template>
  <div class="card h-100 border-0 shadow-sm">
    <div class="card-header bg-white border-0 d-flex justify-content-between align-items-center">
      <h6 class="fw-bold mb-0">Total Employees</h6>
      <button class="btn btn-sm btn-outline-light text-muted border-0">
        <i class="bi bi-three-dots"></i>
      </button>
    </div>
    <div class="card-body">
      <div class="row">
        <div class="col-6">
          <div class="mb-3">
            <div class="d-flex align-items-baseline">
              <h2 class="fw-bold mb-0 me-2">150</h2>
              <span class="badge bg-success-subtle text-success">+50</span>
            </div>
            <small class="text-muted">Fulltime Employee</small>
          </div>
        </div>
        <div class="col-6">
          <div class="mb-3">
            <div class="d-flex align-items-baseline">
              <h2 class="fw-bold mb-0 me-2">50</h2>
              <span class="badge bg-warning-subtle text-warning">+10</span>
            </div>
            <small class="text-muted">Freelance Employee</small>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TotalEmployees'
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

.bg-success-subtle {
  background-color: #d1e7dd !important;
}

.bg-warning-subtle {
  background-color: #fff3cd !important;
}
</style>