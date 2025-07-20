<template>
  <div class="card h-100 border-0 shadow-sm">
    <div class="card-header bg-white border-0 d-flex justify-content-between align-items-center">
      <div>
        <h6 class="fw-bold mb-0">Employee Performance Ratings</h6>
        <small class="text-muted">At Tur Agency, we're proud of our employees' consistent punctuality and quality work</small>
      </div>
      <button class="btn btn-sm btn-outline-light text-muted border-0">
        <i class="bi bi-three-dots"></i>
      </button>
    </div>
    <div class="card-body">
      <div class="d-flex align-items-baseline mb-4">
        <h2 class="fw-bold mb-0">98%</h2>
      </div>

      <!-- Employee Performance Bars -->
      <div class="employee-performance">
        <div v-for="employee in employees" :key="employee.name" class="mb-3">
          <div class="d-flex justify-content-between align-items-center mb-1">
            <small class="fw-medium">{{ employee.name }}</small>
          </div>
          <div class="progress" style="height: 6px;">
            <div class="progress-bar" 
                 :style="{ width: employee.taskCompleted + '%', backgroundColor: '#6c5ce7' }"></div>
            <div class="progress-bar" 
                 :style="{ width: employee.presence + '%', backgroundColor: '#74b9ff' }"></div>
            <div class="progress-bar" 
                 :style="{ width: employee.meeting + '%', backgroundColor: '#00b894' }"></div>
          </div>
        </div>
      </div>

      <!-- Legend -->
      <div class="d-flex justify-content-between mt-4 small text-muted">
        <div class="text-center">
          <span class="badge rounded-pill me-1" style="background-color: #6c5ce7; width: 8px; height: 8px; padding: 0;"></span>
          Task completed
        </div>
        <div class="text-center">
          <span class="badge rounded-pill me-1" style="background-color: #74b9ff; width: 8px; height: 8px; padding: 0;"></span>
          Presence
        </div>
        <div class="text-center">
          <span class="badge rounded-pill me-1" style="background-color: #00b894; width: 8px; height: 8px; padding: 0;"></span>
          Completed Meeting
        </div>
      </div>

      <!-- Scale -->
      <div class="d-flex justify-content-between mt-3 small text-muted">
        <span>0</span>
        <span>5</span>
        <span>10</span>
        <span>15</span>
        <span>20</span>
        <span>25</span>
        <span>30</span>
        <span>35</span>
        <span>40</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'EmployeePerformance',
  data() {
    return {
      employees: [
        { name: 'Ahsan Tapadar', taskCompleted: 85, presence: 10, meeting: 15 },
        { name: 'Koyes Ahmed', taskCompleted: 90, presence: 25, meeting: 20 },
        { name: 'Washi Bin M.', taskCompleted: 75, presence: 15, meeting: 25 },
        { name: 'Mir Muhasin', taskCompleted: 70, presence: 20, meeting: 18 },
        { name: 'Turja Sen Das', taskCompleted: 88, presence: 12, meeting: 22 }
      ]
    }
  }
}
</script>