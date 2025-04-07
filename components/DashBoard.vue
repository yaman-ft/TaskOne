<template>
  <div class="flex items-center justify-center bg-gray-900 bg-opacity-50 md:w-full md:h-full sm:w-1/2 sm:h-1/2 ">
    <!-- Dashboard Container with Animation -->
    <div 
      class="dashboard-container relative bg-white rounded-2xl shadow-xl overflow-hidden transform transition-all duration-500"
      :class="{
        'w-full h-full': isFullscreen,
        'w-96 h-96': !isFullscreen,
        'scale-95': !isFullscreen,
        'scale-100': isFullscreen
      }"
    >
      <!-- Fullscreen Toggle Button -->
      <!-- <button 
        @click="toggleFullscreen"
        class="absolute top-4 right-4 z-10 p-2 rounded-full bg-indigo-100 text-indigo-600 hover:bg-indigo-200 transition-colors"
      >
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" 
            :d="isFullscreen ? 'M6 18L18 6M6 6l12 12' : 'M4 8V4m0 0h4M4 4l5 5m11-1V4m0 0h-4m4 0l-5 5M4 16v4m0 0h4m-4 0l5-5m11 5l-5-5m5 5v-4m0 4h-4'"
          />
        </svg>
      </button> -->

      <!-- Dashboard Content -->
      <div class="h-full flex flex-col ">
<!--   
        <div 
          class="px-6 py-4 bg-indigo-600 text-white flex justify-between items-center transition-all duration-300"
          :class="{
            'h-16': !isFullscreen,
            'h-20': isFullscreen
          }"
        >
          <h1 
            class="font-bold transition-all duration-300"
            :class="{
              'text-lg': !isFullscreen,
              'text-2xl': isFullscreen
            }"
          >
            Indigo Dashboard
          </h1>
          <div class="flex items-center space-x-2">
            <button class="p-1 rounded-full hover:bg-indigo-500 transition-colors">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9" />
              </svg>
            </button>
          </div>
        </div> -->

        <!-- Main Content Area -->
        <div class="flex-1 overflow-auto p-4 bg-gray-50 dark:bg-gray-400">
          <!-- Stats Grid with Animation -->
          <div 
            class="grid gap-4 mb-4 transition-all duration-500 sm:grid-cols-2 md:grid-cols-4"
            :class="{
              'grid-cols-2': !isFullscreen,
              'grid-cols-4': isFullscreen
            }"
          >
            <div 
              v-for="stat in stats" 
              :key="stat.title"
              class="dashboard-card bg-white p-4 rounded-lg shadow-md hover:shadow-lg transition-all duration-300"
             :style="{
                'background': `linear-gradient(135deg, ${stat.bgColor} 0%, ${stat.bgColor2} 100%)`
              }"
              
            >
              <div class="flex items-center">
                <div class="p-2 rounded-full bg-gray-200 bg-opacity-30 dark:bg-gray-900 dark:text-white text-gray-900">
                  <component :is="stat.icon" class="h-5 w-5 text-white " />
                </div>
                <div class="ml-3">
                  <p class="text-xs font-medium text-white text-opacity-80">{{ stat.title }}</p>
                  <p class="text-xl font-semibold text-white">{{ stat.value }}</p>
                </div>
              </div>
              <div class="mt-2">
                <div class="flex items-center justify-between">
                  <span class="text-xs font-medium text-white">
                    {{ stat.change }}
                  </span>
                  <span class="text-xs font-medium text-white text-opacity-80">{{ stat.comparisonText }}</span>
                </div>
              </div>
            </div>
          </div>

          <!-- Charts Area with Animation -->
          <div 
            class="grid gap-4 transition-all duration-500 md:grid-cols-2 sm:grid-cols-1"
            :class="{
              'grid-cols-1': !isFullscreen,
              'grid-cols-2': isFullscreen
            }"
          >
            <!-- Line Chart -->
            <div 
              class="dashboard-card dark:bg-gray-900 dark:text-white bg-white p-4 rounded-lg shadow-md hover:shadow-lg transition-all duration-300"
              :class="{
                'h-48': !isFullscreen,
                'h-64': isFullscreen
              }"
            >
              <h3 class="text-sm font-medium text-gray-700 mb-2 dark:text-stone-50">Revenue Trend</h3>
              <div class="h-full -mt-2 -mx-2 ">
                <canvas ref="lineChart"></canvas>
              </div>
            </div>

            <!-- Bar Chart -->
            <div 
              class="dashboard-card bg-white dark:bg-gray-900 p-4 rounded-lg shadow-md hover:shadow-lg transition-all duration-300"
              :class="{
                'h-48': !isFullscreen,
                'h-64': isFullscreen
              }"
            >
              <h3 class="text-sm font-medium text-gray-700 mb-2 dark:text-stone-50">Monthly Sales</h3>
              <div class="h-full -mt-2 -mx-2 ">
                <canvas ref="barChart"></canvas>
              </div>
            </div>
          </div>

          <!-- Data Table (Only shown in fullscreen) -->
          <div 
            v-if="isFullscreen"
            class="mt-4 bg-white rounded-lg shadow-md overflow-hidden transition-all duration-500 dark:bg-gray-900 dark:text-white"
          >
            <div class="px-4 py-3 border-b border-gray-200 dark:bg-gray-900 dark:text-white">
              <h3 class="text-sm font-medium text-gray-700">Recent Transactions</h3>
            </div>
            <div class="overflow-x-auto">
              <table class="min-w-full divide-y divide-gray-200 dark:bg-gray-900 dark:text-white">
                <thead class="bg-gray-50 dark:bg-gray-800 dark:text-white">
                  <tr>
                    <th v-for="header in tableHeaders" :key="header" scope="col" class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                      {{ header }}
                    </th>
                  </tr>
                </thead>
                <tbody class="bg-white divide-y divide-gray-200 dark:bg-gray-800 dark:text-white">
                  <tr 
                    v-for="(row, index) in transactions" 
                    :key="index"
                    class="hover:bg-gray-50 transition-colors duration-150"
                  >
                    <td v-for="(value, key) in row" :key="key" class="px-4 py-2 whitespace-nowrap text-sm text-gray-500">
                      {{ value }}
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue'
import Chart from 'chart.js/auto'
import {
  ChartBarIcon,
  UserGroupIcon,
  ShoppingCartIcon,
  FolderIcon
} from '@heroicons/vue/outline'

export default {
  setup() {
    const isFullscreen = ref(true)
    const lineChart = ref(null)
    const barChart = ref(null)

 const stats = [
      { 
        title: 'Total Revenue', 
        value: '$24,780', 
        change: '+12.5%', 
        comparisonText: 'vs last month',
        icon: ChartBarIcon,
        bgColor: '#6366f1',
        bgColor2: '#8b5cf6'
      },
      { 
        title: 'New Users', 
        value: '1,254', 
        change: '+3.2%', 
        comparisonText: 'vs last month',
        icon: UserGroupIcon,
        bgColor: '#a038a3',
        bgColor2: '#782a7a'
      },
      { 
        title: 'Pending Orders', 
        value: '56', 
        change: '+2.4%', 
        comparisonText: 'vs last month',
        icon: ShoppingCartIcon,
        bgColor: '#412a7a',
        bgColor2: '#593ca3'
      },
      { 
        title: 'Active Projects', 
        value: '24', 
        change: '+4.3%', 
        comparisonText: 'vs last month',
        icon: FolderIcon,
        bgColor: '#3b82f6',
        bgColor2: '#2563eb'
      }
    ]


    const tableHeaders = ['ID', 'Customer', 'Date', 'Amount', 'Status']
    const transactions = [
      { id: '#TRX-001', customer: 'John Smith', date: '2023-07-15', amount: '$125.00', status: 'Completed' },
      { id: '#TRX-002', customer: 'Sarah Johnson', date: '2023-07-14', amount: '$89.50', status: 'Pending' },
      { id: '#TRX-003', customer: 'Michael Brown', date: '2023-07-14', amount: '$245.75', status: 'Completed' },
      { id: '#TRX-004', customer: 'Emily Davis', date: '2023-07-13', amount: '$67.30', status: 'Failed' },
      { id: '#TRX-005', customer: 'Robert Wilson', date: '2023-07-12', amount: '$189.00', status: 'Completed' }
    ]

    const toggleFullscreen = () => {
      isFullscreen.value = !isFullscreen.value
    }

    const renderCharts = () => {
      // Destroy existing charts if they exist
      if (lineChart.value && lineChart.value.chart) {
        lineChart.value.chart.destroy()
      }
      if (barChart.value && barChart.value.chart) {
        barChart.value.chart.destroy()
      }

      // Line Chart
      const lineCtx = lineChart.value.getContext('2d')
      lineChart.value.chart = new Chart(lineCtx, {
        type: 'line',
        data: {
          labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul'],
          datasets: [
            {
              label: '2023',
              data: [65, 59, 80, 81, 56, 55, 40],
              fill: false,
              backgroundColor: '#4f46e5',
              borderColor: '#4f46e5',
              tension: 0.3,
              borderWidth: 2,
              pointBackgroundColor: '#fff',
              pointBorderColor: '#4f46e5',
              pointBorderWidth: 2,
              pointRadius: 4,
              pointHoverRadius: 6
            }
          ]
        },
        options: {
          responsive: true,
          maintainAspectRatio: false,
          plugins: {
            legend: {
              display: false
            }
          },
          scales: {
            y: {
              beginAtZero: true,
              grid: {
                drawBorder: false,
                color: 'rgba(0, 0, 0, 0.05)'
              },
              ticks: {
                color: '#6b7280'
              }
            },
            x: {
              grid: {
                display: false
              },
              ticks: {
                color: '#6b7280'
              }
            }
          }
        }
      })

      // Bar Chart
      const barCtx = barChart.value.getContext('2d')
      barChart.value.chart = new Chart(barCtx, {
        type: 'bar',
        data: {
          labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul'],
          datasets: [
            {
              label: 'Sales',
              data: [12, 19, 3, 5, 2, 3, 15],
              backgroundColor: '#4f46e5',
              borderColor: '#4f46e5',
              borderWidth: 0,
              borderRadius: 4,
              hoverBackgroundColor: '#4338ca'
            }
          ]
        },
        options: {
          responsive: true,
          maintainAspectRatio: false,
          plugins: {
            legend: {
              display: false
            }
          },
          scales: {
            y: {
              beginAtZero: true,
              grid: {
                drawBorder: false,
                color: 'rgba(0, 0, 0, 0.05)'
              },
              ticks: {
                color: '#6b7280'
              }
            },
            x: {
              grid: {
                display: false
              },
              ticks: {
                color: '#6b7280'
              }
            }
          }
        }
      })
    }

    onMounted(() => {
      renderCharts();
      if ( window.innerWidth <= 1000 )
      {
        isFullscreen.value = false;
      }
    })

    return {
      isFullscreen,
      toggleFullscreen,
      stats,
      tableHeaders,
      transactions,
      lineChart,
      barChart,
      ChartBarIcon,
      UserGroupIcon,
      ShoppingCartIcon,
      FolderIcon
    }
  }
}
</script>

<style>
.dashboard-container {
  transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
}

.dashboard-card {
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

/* Custom scrollbar for the dashboard */
.dashboard-container ::-webkit-scrollbar {
  width: 6px;
  height: 6px;
}

.dashboard-container ::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 3px;
}

.dashboard-container ::-webkit-scrollbar-thumb {
  background: #c7d2fe;
  border-radius: 3px;
}

.dashboard-container ::-webkit-scrollbar-thumb:hover {
  background: #a5b4fc;
  
}

/* Animation for stats cards */
@keyframes float {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-5px);
  }
}

.dashboard-card:hover {
  animation: float 2s ease-in-out infinite;
}
</style>