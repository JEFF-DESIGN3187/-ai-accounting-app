<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>AI 自动记账 APP 原型</title>
  <!-- 引入 Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- 引入 Font Awesome -->
  <link href="https://cdn.jsdelivr.net/npm/font-awesome@4.7.0/css/font-awesome.min.css" rel="stylesheet">
  <!-- 引入 Chart.js -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.8/dist/chart.umd.min.js"></script>
  
  <!-- Tailwind 配置 -->
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            primary: '#165DFF',
            secondary: '#36D399',
            danger: '#F87272',
            neutral: '#1E293B',
            'neutral-light': '#94A3B8',
            'neutral-lighter': '#F1F5F9',
          },
          fontFamily: {
            inter: ['Inter', 'sans-serif'],
          },
        },
      }
    }
  </script>
  
  <!-- 自定义工具类 -->
  <style type="text/tailwindcss">
    @layer utilities {
      .content-auto {
        content-visibility: auto;
      }
      .card-shadow {
        box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
      }
      .card-hover {
        transition: all 0.3s ease;
      }
      .card-hover:hover {
        transform: translateY(-5px);
        box-shadow: 0 10px 25px rgba(22, 93, 255, 0.12);
      }
      .btn-hover {
        transition: all 0.2s ease;
      }
      .btn-hover:hover {
        transform: translateY(-2px);
      }
    }
  </style>
  
  <!-- 引入 Inter 字体 -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
</head>
<body class="bg-gray-50 font-inter text-neutral">
  <div class="container mx-auto p-4 md:p-8">
    <h1 class="text-[clamp(1.5rem,3vw,2.5rem)] font-bold text-center mb-8 text-neutral">AI 自动记账 APP 原型设计</h1>
    
    <!-- 页面原型网格 -->
    <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
      
      <!-- 仪表盘页面 -->
      <div class="bg-white rounded-2xl overflow-hidden card-shadow h-[700px] relative">
        <!-- 顶部导航栏 -->
        <div class="bg-primary text-white p-4 flex items-center justify-between">
          <div class="flex items-center space-x-2">
            <i class="fa fa-line-chart text-xl"></i>
            <h2 class="font-semibold text-lg">财务仪表盘</h2>
          </div>
          <div class="flex space-x-4">
            <button class="p-1 rounded-full hover:bg-primary/80 transition">
              <i class="fa fa-bell-o"></i>
            </button>
            <button class="p-1 rounded-full hover:bg-primary/80 transition">
              <i class="fa fa-cog"></i>
            </button>
          </div>
        </div>
        
        <!-- 主内容区 -->
        <div class="p-5 overflow-y-auto h-[calc(100%-56px)]">
          <!-- 欢迎信息 -->
          <div class="mb-6">
            <p class="text-neutral-light">早上好，用户</p>
            <h3 class="text-xl font-bold">这是您的财务概览</h3>
          </div>
          
          <!-- 余额卡片 -->
          <div class="bg-gradient-to-r from-primary to-blue-600 text-white p-5 rounded-xl mb-6">
            <div class="flex justify-between items-center mb-3">
              <p class="text-sm opacity-80">当前余额</p>
              <button class="text-xs bg-white/20 px-2 py-1 rounded-full">
                <i class="fa fa-refresh mr-1"></i>更新
              </button>
            </div>
            <p class="text-3xl font-bold">¥24,568.25</p>
            <div class="flex justify-between text-xs mt-4">
              <div>
                <p class="opacity-80">本月收入</p>
                <p class="text-secondary">¥8,450.00</p>
              </div>
              <div>
                <p class="opacity-80">本月支出</p>
                <p class="text-danger">¥3,280.50</p>
              </div>
              <div>
                <p class="opacity-80">节省</p>
                <p class="text-secondary">¥5,169.50</p>
              </div>
            </div>
          </div>
          
          <!-- 快捷操作 -->
          <div class="grid grid-cols-4 gap-3 mb-6">
            <button class="bg-neutral-lighter rounded-xl p-3 flex flex-col items-center card-hover">
              <div class="w-10 h-10 rounded-full bg-primary/10 flex items-center justify-center mb-2">
                <i class="fa fa-plus text-primary"></i>
              </div>
              <span class="text-xs font-medium">添加</span>
            </button>
            <button class="bg-neutral-lighter rounded-xl p-3 flex flex-col items-center card-hover">
              <div class="w-10 h-10 rounded-full bg-secondary/10 flex items-center justify-center mb-2">
                <i class="fa fa-arrow-down text-secondary"></i>
              </div>
              <span class="text-xs font-medium">收入</span>
            </button>
            <button class="bg-neutral-lighter rounded-xl p-3 flex flex-col items-center card-hover">
              <div class="w-10 h-10 rounded-full bg-danger/10 flex items-center justify-center mb-2">
                <i class="fa fa-arrow-up text-danger"></i>
              </div>
              <span class="text-xs font-medium">支出</span>
            </button>
            <button class="bg-neutral-lighter rounded-xl p-3 flex flex-col items-center card-hover">
              <div class="w-10 h-10 rounded-full bg-blue-100 flex items-center justify-center mb-2">
                <i class="fa fa-qrcode text-blue-600"></i>
              </div>
              <span class="text-xs font-medium">扫码</span>
            </button>
          </div>
          
          <!-- 图表 -->
          <div class="bg-white rounded-xl p-4 mb-6 card-shadow">
            <div class="flex justify-between items-center mb-4">
              <h4 class="font-semibold">月度收支</h4>
              <div class="flex space-x-2">
                <button class="px-3 py-1 text-xs rounded-full bg-primary text-white">月</button>
                <button class="px-3 py-1 text-xs rounded-full bg-neutral-lighter">季</button>
                <button class="px-3 py-1 text-xs rounded-full bg-neutral-lighter">年</button>
              </div>
            </div>
            <div class="h-48">
              <canvas id="incomeExpenseChart"></canvas>
            </div>
          </div>
          
          <!-- 最近交易 -->
          <div class="bg-white rounded-xl p-4 card-shadow">
            <div class="flex justify-between items-center mb-4">
              <h4 class="font-semibold">最近交易</h4>
              <a href="#" class="text-primary text-sm">查看全部</a>
            </div>
            
            <!-- 交易列表 -->
            <div class="space-y-3">
              <div class="flex items-center p-2 rounded-lg hover:bg-neutral-lighter/50 transition">
                <div class="w-10 h-10 rounded-full bg-red-100 flex items-center justify-center mr-3">
                  <i class="fa fa-cutlery text-danger"></i>
                </div>
                <div class="flex-1">
                  <p class="font-medium">午餐</p>
                  <p class="text-xs text-neutral-light">今天 12:30</p>
                </div>
                <p class="font-medium text-danger">-¥58.00</p>
              </div>
              
              <div class="flex items-center p-2 rounded-lg hover:bg-neutral-lighter/50 transition">
                <div class="w-10 h-10 rounded-full bg-green-100 flex items-center justify-center mr-3">
                  <i class="fa fa-briefcase text-secondary"></i>
                </div>
                <div class="flex-1">
                  <p class="font-medium">工资</p>
                  <p class="text-xs text-neutral-light">昨天 09:15</p>
                </div>
                <p class="font-medium text-secondary">+¥8,000.00</p>
              </div>
              
              <div class="flex items-center p-2 rounded-lg hover:bg-neutral-lighter/50 transition">
                <div class="w-10 h-10 rounded-full bg-blue-100 flex items-center justify-center mr-3">
                  <i class="fa fa-shopping-bag text-blue-600"></i>
                </div>
                <div class="flex-1">
                  <p class="font-medium">超市购物</p>
                  <p class="text-xs text-neutral-light">昨天 18:45</p>
                </div>
                <p class="font-medium text-danger">-¥245.50</p>
              </div>
              
              <div class="flex items-center p-2 rounded-lg hover:bg-neutral-lighter/50 transition">
                <div class="w-10 h-10 rounded-full bg-purple-100 flex items-center justify-center mr-3">
                  <i class="fa fa-home text-purple-600"></i>
                </div>
                <div class="flex-1">
                  <p class="font-medium">房租</p>
                  <p class="text-xs text-neutral-light">3月1日 08:00</p>
                </div>
                <p class="font-medium text-danger">-¥2,500.00</p>
              </div>
            </div>
          </div>
        </div>
        
        <!-- 底部导航 -->
        <div class="absolute bottom-0 left-0 right-0 bg-white border-t border-gray-100 py-2 px-4">
          <div class="grid grid-cols-4 gap-2">
            <button class="flex flex-col items-center text-primary">
              <i class="fa fa-dashboard"></i>
              <span class="text-xs mt-1">仪表盘</span>
            </button>
            <button class="flex flex-col items-center text-neutral-light">
              <i class="fa fa-pie-chart"></i>
              <span class="text-xs mt-1">分析</span>
            </button>
            <button class="flex flex-col items-center text-neutral-light">
              <i class="fa fa-plus-circle text-2xl"></i>
              <span class="text-xs mt-1">记账</span>
            </button>
            <button class="flex flex-col items-center text-neutral-light">
              <i class="fa fa-user-o"></i>
              <span class="text-xs mt-1">我的</span>
            </button>
          </div>
        </div>
      </div>
      
      <!-- 记账页面 -->
      <div class="bg-white rounded-2xl overflow-hidden card-shadow h-[700px] relative">
        <!-- 顶部导航栏 -->
        <div class="bg-primary text-white p-4 flex items-center justify-between">
          <div class="flex items-center space-x-2">
            <button class="p-1 rounded-full hover:bg-primary/80 transition">
              <i class="fa fa-arrow-left"></i>
            </button>
            <h2 class="font-semibold text-lg">添加记账</h2>
          </div>
          <button class="bg-white text-primary px-4 py-1 rounded-lg font-medium btn-hover">
            保存
          </button>
        </div>
        
        <!-- 主内容区 -->
        <div class="p-5 overflow-y-auto h-[calc(100%-56px)]">
          <!-- 支出/收入切换 -->
          <div class="flex mb-6">
            <button class="flex-1 py-3 bg-danger/10 text-danger rounded-l-lg font-medium">
              支出
            </button>
            <button class="flex-1 py-3 bg-neutral-lighter text-neutral-light rounded-r-lg font-medium">
              收入
            </button>
          </div>
          
          <!-- 金额输入 -->
          <div class="mb-8 text-center">
            <p class="text-neutral-light mb-1">金额</p>
            <input type="text" value="58.00" class="text-4xl font-bold text-center border-b-2 border-gray-200 w-1/2 mx-auto focus:outline-none focus:border-primary transition">
          </div>
          
          <!-- 分类选择 -->
          <div class="mb-8">
            <p class="text-neutral-light mb-3">分类</p>
            <div class="grid grid-cols-4 gap-3">
              <button class="bg-red-100 text-danger p-3 rounded-xl flex flex-col items-center card-hover">
                <i class="fa fa-cutlery text-xl mb-2"></i>
                <span class="text-xs">餐饮</span>
              </button>
              <button class="bg-neutral-lighter p-3 rounded-xl flex flex-col items-center card-hover">
                <i class="fa fa-coffee text-xl mb-2"></i>
                <span class="text-xs">饮料</span>
              </button>
              <button class="bg-neutral-lighter p-3 rounded-xl flex flex-col items-center card-hover">
                <i class="fa fa-shopping-bag text-xl mb-2"></i>
                <span class="text-xs">购物</span>
              </button>
              <button class="bg-neutral-lighter p-3 rounded-xl flex flex-col items-center card-hover">
                <i class="fa fa-home text-xl mb-2"></i>
                <span class="text-xs">住房</span>
              </button>
              <button class="bg-neutral-lighter p-3 rounded-xl flex flex-col items-center card-hover">
                <i class="fa fa-car text-xl mb-2"></i>
                <span class="text-xs">交通</span>
              </button>
              <button class="bg-neutral-lighter p-3 rounded-xl flex flex-col items-center card-hover">
                <i class="fa fa-film text-xl mb-2"></i>
                <span class="text-xs">娱乐</span>
              </button>
              <button class="bg-neutral-lighter p-3 rounded-xl flex flex-col items-center card-hover">
                <i class="fa fa-heartbeat text-xl mb-2"></i>
                <span class="text-xs">医疗</span>
              </button>
              <button class="bg-neutral-lighter p-3 rounded-xl flex flex-col items-center card-hover">
                <i class="fa fa-ellipsis-h text-xl mb-2"></i>
                <span class="text-xs">更多</span>
              </button>
            </div>
          </div>
          
          <!-- 日期和备注 -->
          <div class="space-y-5 mb-8">
            <div>
              <p class="text-neutral-light mb-2">日期</p>
              <div class="flex items-center bg-neutral-lighter p-3 rounded-lg">
                <i class="fa fa-calendar text-neutral-light mr-3"></i>
                <input type="date" class="bg-transparent flex-1 focus:outline-none">
              </div>
            </div>
            
            <div>
              <p class="text-neutral-light mb-2">时间</p>
              <div class="flex items-center bg-neutral-lighter p-3 rounded-lg">
                <i class="fa fa-clock-o text-neutral-light mr-3"></i>
                <input type="time" class="bg-transparent flex-1 focus:outline-none">
              </div>
            </div>
            
            <div>
              <p class="text-neutral-light mb-2">备注</p>
              <div class="flex items-start bg-neutral-lighter p-3 rounded-lg">
                <i class="fa fa-pencil text-neutral-light mr-3 mt-1"></i>
                <textarea class="bg-transparent flex-1 focus:outline-none" rows="2" placeholder="添加备注..."></textarea>
              </div>
            </div>
          </div>
          
          <!-- AI 助手建议 -->
          <div class="bg-primary/5 border border-primary/20 rounded-xl p-4 mb-8">
            <div class="flex items-start">
              <div class="w-8 h-8 rounded-full bg-primary text-white flex items-center justify-center mr-3 flex-shrink-0">
                <i class="fa fa-robot"></i>
              </div>
              <div>
                <h4 class="font-medium text-primary mb-1">AI 建议</h4>
                <p class="text-sm text-neutral-light">根据您的消费习惯，您可以考虑将此归类为"工作餐"，这样可以更好地跟踪您的工作相关支出。</p>
              </div>
            </div>
          </div>
          
          <!-- 支付方式 -->
          <div class="mb-8">
            <p class="text-neutral-light mb-3">支付方式</p>
            <div class="grid grid-cols-3 gap-3">
              <button class="bg-neutral-lighter p-3 rounded-xl flex items-center card-hover">
                <i class="fa fa-credit-card text-xl mr-2"></i>
                <span class="text-sm">银行卡</span>
              </button>
              <button class="bg-neutral-lighter p-3 rounded-xl flex items-center card-hover">
                <i class="fa fa-wechat text-xl mr-2"></i>
                <span class="text-sm">微信</span>
              </button>
              <button class="bg-neutral-lighter p-3 rounded-xl flex items-center card-hover">
                <i class="fa fa-qq text-xl mr-2"></i>
                <span class="text-sm">支付宝</span>
              </button>
            </div>
          </div>
        </div>
        
        <!-- 底部导航 -->
        <div class="absolute bottom-0 left-0 right-0 bg-white border-t border-gray-100 py-2 px-4">
          <div class="grid grid-cols-4 gap-2">
            <button class="flex flex-col items-center text-neutral-light">
              <i class="fa fa-dashboard"></i>
              <span class="text-xs mt-1">仪表盘</span>
            </button>
            <button class="flex flex-col items-center text-neutral-light">
              <i class="fa fa-pie-chart"></i>
              <span class="text-xs mt-1">分析</span>
            </button>
            <button class="flex flex-col items-center text-primary">
              <i class="fa fa-plus-circle text-2xl"></i>
              <span class="text-xs mt-1">记账</span>
            </button>
            <button class="flex flex-col items-center text-neutral-light">
              <i class="fa fa-user-o"></i>
              <span class="text-xs mt-1">我的</span>
            </button>
          </div>
        </div>
      </div>
      
      <!-- 消费分析页面 -->
      <div class="bg-white rounded-2xl overflow-hidden card-shadow h-[700px] relative">
        <!-- 顶部导航栏 -->
        <div class="bg-primary text-white p-4 flex items-center justify-between">
          <div class="flex items-center space-x-2">
            <i class="fa fa-pie-chart text-xl"></i>
            <h2 class="font-semibold text-lg">消费分析</h2>
          </div>
          <div class="flex space-x-4">
            <button class="p-1 rounded-full hover:bg-primary/80 transition">
              <i class="fa fa-download"></i>
            </button>
            <button class="p-1 rounded-full hover:bg-primary/80 transition">
              <i class="fa fa-share-alt"></i>
            </button>
          </div>
        </div>
        
        <!-- 主内容区 -->
        <div class="p-5 overflow-y-auto h-[calc(100%-56px)]">
          <!-- 筛选器 -->
          <div class="flex justify-between items-center mb-6">
            <div class="flex space-x-2">
              <button class="px-4 py-1.5 text-sm rounded-full bg-primary text-white">
                本月
              </button>
              <button class="px-4 py-1.5 text-sm rounded-full bg-neutral-lighter">
                上月
              </button>
              <button class="px-4 py-1.5 text-sm rounded-full bg-neutral-lighter">
                全年
              </button>
            </div>
            <button class="flex items-center text-sm text-primary">
              <i class="fa fa-filter mr-1"></i> 筛选
            </button>
          </div>
          
          <!-- 总览卡片 -->
          <div class="grid grid-cols-2 gap-4 mb-6">
            <div class="bg-white p-4 rounded-xl card-shadow">
              <p class="text-neutral-light text-sm mb-1">总收入</p>
              <p class="text-2xl font-bold">¥8,450.00</p>
              <p class="text-xs text-secondary mt-1">
                <i class="fa fa-arrow-up mr-1"></i> 12.5% 较上月
              </p>
            </div>
            
            <div class="bg-white p-4 rounded-xl card-shadow">
              <p class="text-neutral-light text-sm mb-1">总支出</p>
              <p class="text-2xl font-bold text-danger">¥3,280.50</p>
              <p class="text-xs text-danger mt-1">
                <i class="fa fa-arrow-up mr-1"></i> 8.2% 较上月
              </p>
            </div>
          </div>
          
          <!-- 支出分类饼图 -->
          <div class="bg-white rounded-xl p-4 mb-6 card-shadow">
            <div class="flex justify-between items-center mb-4">
              <h4 class="font-semibold">支出分类</h4>
              <button class="text-xs text-primary">
                查看详情
              </button>
            </div>
            <div class="flex">
              <div class="w-1/2 h-48">
                <canvas id="expenseCategoryChart"></canvas>
              </div>
              <div class="w-1/2 pl-4">
                <div class="space-y-3">
                  <div>
                    <div class="flex justify-between mb-1">
                      <span class="text-sm font-medium">餐饮</span>
                      <span class="text-sm">35%</span>
                    </div>
                    <div class="w-full bg-gray-100 rounded-full h-1.5">
                      <div class="bg-red-500 h-1.5 rounded-full" style="width: 35%"></div>
                    </div>
                  </div>
                  
                  <div>
                    <div class="flex justify-between mb-1">
                      <span class="text-sm font-medium">购物</span>
                      <span class="text-sm">25%</span>
                    </div>
                    <div class="w-full bg-gray-100 rounded-full h-1.5">
                      <div class="bg-blue-500 h-1.5 rounded-full" style="width: 25%"></div>
                    </div>
                  </div>
                  
                  <div>
                    <div class="flex justify-between mb-1">
                      <span class="text-sm font-medium">住房</span>
                      <span class="text-sm">20%</span>
                    </div>
                    <div class="w-full bg-gray-100 rounded-full h-1.5">
                      <div class="bg-purple-500 h-1.5 rounded-full" style="width: 20%"></div>
                    </div>
                  </div>
                  
                  <div>
                    <div class="flex justify-between mb-1">
                      <span class="text-sm font-medium">交通</span>
                      <span class="text-sm">15%</span>
                    </div>
                    <div class="w-full bg-gray-100 rounded-full h-1.5">
                      <div class="bg-green-500 h-1.5 rounded-full" style="width: 15%"></div>
                    </div>
                  </div>
                  
                  <div>
                    <div class="flex justify-between mb-1">
                      <span class="text-sm font-medium">其他</span>
                      <span class="text-sm">5%</span>
                    </div>
                    <div class="w-full bg-gray-100 rounded-full h-1.5">
                      <div class="bg-gray-500 h-1.5 rounded-full" style="width: 5%"></div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          
          <!-- 趋势图表 -->
          <div class="bg-white rounded-xl p-4 mb-6 card-shadow">
            <div class="flex justify-between items-center mb-4">
              <h4 class="font-semibold">月度趋势</h4>
              <div class="flex space-x-2">
                <button class="px-3 py-1 text-xs rounded-full bg-primary text-white">收入</button>
                <button class="px-3 py-1 text-xs rounded-full bg-neutral-lighter">支出</button>
              </div>
            </div>
            <div class="h-48">
              <canvas id="monthlyTrendChart"></canvas>
            </div>
          </div>
          
          <!-- AI 洞察 -->
          <div class="bg-secondary/5 border border-secondary/20 rounded-xl p-4 mb-6">
            <div class="flex items-start">
              <div class="w-8 h-8 rounded-full bg-secondary text-white flex items-center justify-center mr-3 flex-shrink-0">
                <i class="fa fa-lightbulb-o"></i>
              </div>
              <div>
                <h4 class="font-medium text-secondary mb-1">AI 洞察</h4>
                <p class="text-sm text-neutral-light">本月您的餐饮支出较上月增加了 15%，建议控制外出就餐频率以节省开支。</p>
              </div>
            </div>
          </div>
          
          <!-- 预算追踪 -->
          <div class="bg-white rounded-xl p-4 mb-6 card-shadow">
            <div class="flex justify-between items-center mb-4">
              <h4 class="font-semibold">预算追踪</h4>
              <button class="text-xs text-primary">
                管理预算
              </button>
            </div>
            <div class="space-y-4">
              <div>
                <div class="flex justify-between mb-1">
                  <span class="text-sm font-medium">餐饮</span>
                  <span class="text-sm text-danger">¥1,200 / ¥1,000</span>
                </div>
                <div class="w-full bg-gray-100 rounded-full h-2">
                  <div class="bg-red-500 h-2 rounded-full" style="width: 120%"></div>
                </div>
              </div>
              
              <div>
                <div class="flex justify-between mb-1">
                  <span class="text-sm font-medium">购物</span>
                  <span class="text-sm text-green-600">¥800 / ¥1,500</span>
                </div>
                <div class="w-full bg-gray-100 rounded-full h-2">
                  <div class="bg-green-500 h-2 rounded-full" style="width: 53%"></div>
                </div>
              </div>
              
              <div>
                <div class="flex justify-between mb-1">
                  <span class="text-sm font-medium">交通</span>
                  <span class="text-sm text-green-600">¥300 / ¥500</span>
                </div>
                <div class="w-full bg-gray-100 rounded-full h-2">
                  <div class="bg-blue-500 h-2 rounded-full" style="width: 60%"></div>
                </div>
              </div>
            </div>
          </div>
        </div>
        
        <!-- 底部导航 -->
        <div class="absolute bottom-0 left-0 right-0 bg-white border-t border-gray-100 py-2 px-4">
          <div class="grid grid-cols-4 gap-2">
            <button class="flex flex-col items-center text-neutral-light">
              <i class="fa fa-dashboard"></i>
              <span class="text-xs mt-1">仪表盘</span>
            </button>
            <button class="flex flex-col items-center text-primary">
              <i class="fa fa-pie-chart"></i>
              <span class="text-xs mt-1">分析</span>
            </button>
            <button class="flex flex-col items-center text-neutral-light">
              <i class="fa fa-plus-circle text-2xl"></i>
              <span class="text-xs mt-1">记账</span>
            </button>
            <button class="flex flex-col items-center text-neutral-light">
              <i class="fa fa-user-o"></i>
              <span class="text-xs mt-1">我的</span>
            </button>
          </div>
        </div>
      </div>
      
      <!-- 设置页面 -->
      <div class="bg-white rounded-2xl overflow-hidden card-shadow h-[700px] relative">
        <!-- 顶部导航栏 -->
        <div class="bg-primary text-white p-4 flex items-center justify-between">
          <div class="flex items-center space-x-2">
            <i class="fa fa-cog text-xl"></i>
            <h2 class="font-semibold text-lg">设置</h2>
          </div>
          <button class="p-1 rounded-full hover:bg-primary/80 transition">
            <i class="fa fa-question-circle"></i>
          </button>
        </div>
        
        <!-- 主内容区 -->
        <div class="p-5 overflow-y-auto h-[calc(100%-56px)]">
          <!-- 用户信息 -->
          <div class="flex items-center mb-8 pb-4 border-b border-gray-100">
            <div class="w-16 h-16 rounded-full bg-neutral-lighter flex items-center justify-center mr-4">
              <img src="https://picsum.photos/id/1005/200/200" alt="用户头像" class="w-full h-full object-cover rounded-full">
            </div>
            <div>
              <h3 class="font-bold text-lg">张小明</h3>
              <p class="text-sm text-neutral-light">zhangxiaoming@example.com</p>
              <button class="text-xs text-primary mt-1">
                <i class="fa fa-pencil mr-1"></i> 编辑资料
              </button>
            </div>
          </div>
          
          <!-- 设置列表 -->
          <div class="space-y-6">
            <!-- 账户设置 -->
            <div>
              <h4 class="text-sm font-medium text-neutral-light mb-3">账户设置</h4>
              <div class="space-y-3">
                <button class="flex justify-between items-center w-full bg-white p-4 rounded-xl card-shadow card-hover">
                  <div class="flex items-center">
                    <div class="w-10 h-10 rounded-full bg-blue-100 flex items-center justify-center mr-3">
                      <i class="fa fa-credit-card text-blue-600"></i>
                    </div>
                    <span>支付方式</span>
                  </div>
                  <i class="fa fa-chevron-right text-neutral-light"></i>
                </button>
                
                <button class="flex justify-between items-center w-full bg-white p-4 rounded-xl card-shadow card-hover">
                  <div class="flex items-center">
                    <div class="w-10 h-10 rounded-full bg-green-100 flex items-center justify-center mr-3">
                      <i class="fa fa-bank text-green-600"></i>
                    </div>
                    <span>关联银行卡</span>
                  </div>
                  <i class="fa fa-chevron-right text-neutral-light"></i>
                </button>
                
                <button class="flex justify-between items-center w-full bg-white p-4 rounded-xl card-shadow card-hover">
                  <div class="flex items-center">
                    <div class="w-10 h-10 rounded-full bg-purple-100 flex items-center justify-center mr-3">
                      <i class="fa fa-lock text-purple-600"></i>
                    </div>
                    <span>密码管理</span>
                  </div>
                  <i class="fa fa-chevron-right text-neutral-light"></i>
                </button>
              </div>
            </div>
            
            <!-- 通知设置 -->
            <div>
              <h4 class="text-sm font-medium text-neutral-light mb-3">通知设置</h4>
              <div class="space-y-3">
                <div class="flex justify-between items-center w-full bg-white p-4 rounded-xl card-shadow">
                  <div class="flex items-center">
                    <div class="w-10 h-10 rounded-full bg-yellow-100 flex items-center justify-center mr-3">
                      <i class="fa fa-bell text-yellow-600"></i>
                    </div>
                    <span>消息通知</span>
                  </div>
                  <label class="relative inline-flex items-center cursor-pointer">
                    <input type="checkbox" value="" class="sr-only peer" checked>
                    <div class="w-11 h-6 bg-gray-200 peer-focus:outline-none rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-primary"></div>
                  </label>
                </div>
                
                <div class="flex justify-between items-center w-full bg-white p-4 rounded-xl card-shadow">
                  <div class="flex items-center">
                    <div class="w-10 h-10 rounded-full bg-red-100 flex items-center justify-center mr-3">
                      <i class="fa fa-credit-card text-red-600"></i>
                    </div>
                    <span>消费提醒</span>
                  </div>
                  <label class="relative inline-flex items-center cursor-pointer">
                    <input type="checkbox" value="" class="sr-only peer" checked>
                    <div class="w-11 h-6 bg-gray-200 peer-focus:outline-none rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-primary"></div>
                  </label>
                </div>
                
                <div class="flex justify-between items-center w-full bg-white p-4 rounded-xl card-shadow">
                  <div class="flex items-center">
                    <div class="w-10 h-10 rounded-full bg-green-100 flex items-center justify-center mr-3">
                      <i class="fa fa-calendar-check-o text-green-600"></i>
                    </div>
                    <span>账单提醒</span>
                  </div>
                  <label class="relative inline-flex items-center cursor-pointer">
                    <input type="checkbox" value="" class="sr-only peer">
                    <div class="w-11 h-6 bg-gray-200 peer-focus:outline-none rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-primary"></div>
                  </label>
                </div>
              </div>
            </div>
            
            <!-- AI 设置 -->
            <div>
              <h4 class="text-sm font-medium text-neutral-light mb-3">AI 设置</h4>
              <div class="space-y-3">
                <div class="flex justify-between items-center w-full bg-white p-4 rounded-xl card-shadow">
                  <div class="flex items-center">
                    <div class="w-10 h-10 rounded-full bg-primary/10 flex items-center justify-center mr-3">
                      <i class="fa fa-robot text-primary"></i>
                    </div>
                    <span>AI 自动分类</span>
                  </div>
                  <label class="relative inline-flex items-center cursor-pointer">
                    <input type="checkbox" value="" class="sr-only peer" checked>
                    <div class="w-11 h-6 bg-gray-200 peer-focus:outline-none rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-primary"></div>
                  </label>
                </div>
                
                <div class="flex justify-between items-center w-full bg-white p-4 rounded-xl card-shadow">
                  <div class="flex items-center">
                    <div class="w-10 h-10 rounded-full bg-primary/10 flex items-center justify-center mr-3">
                      <i class="fa fa-line-chart text-primary"></i>
                    </div>
                    <span>智能分析</span>
                  </div>
                  <label class="relative inline-flex items-center cursor-pointer">
                    <input type="checkbox" value="" class="sr-only peer" checked>
                    <div class="w-11 h-6 bg-gray-200 peer-focus:outline-none rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-primary"></div>
                  </label>
                </div>
                
                <div class="flex justify-between items-center w-full bg-white p-4 rounded-xl card-shadow">
                  <div class="flex items-center">
                    <div class="w-10 h-10 rounded-full bg-primary/10 flex items-center justify-center mr-3">
                      <i class="fa fa-lightbulb-o text-primary"></i>
                    </div>
                    <span>财务建议</span>
                  </div>
                  <label class="relative inline-flex items-center cursor-pointer">
                    <input type="checkbox" value="" class="sr-only peer">
                    <div class="w-11 h-6 bg-gray-200 peer-focus:outline-none rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-primary"></div>
                  </label>
                </div>
              </div>
            </div>
            
            <!-- 关于 -->
            <div>
              <h4 class="text-sm font-medium text-neutral-light mb-3">关于</h4>
              <div class="space-y-3">
                <button class="flex justify-between items-center w-full bg-white p-4 rounded-xl card-shadow card-hover">
                  <div class="flex items-center">
                    <div class="w-10 h-10 rounded-full bg-gray-100 flex items-center justify-center mr-3">
                      <i class="fa fa-info-circle text-gray-600"></i>
                    </div>
                    <span>关于我们</span>
                  </div>
                  <i class="fa fa-chevron-right text-neutral-light"></i>
                </button>
                
                <button class="flex justify-between items-center w-full bg-white p-4 rounded-xl card-shadow card-hover">
                  <div class="flex items-center">
                    <div class="w-10 h-10 rounded-full bg-gray-100 flex items-center justify-center mr-3">
                      <i class="fa fa-shield text-gray-600"></i>
                    </div>
                    <span>隐私政策</span>
                  </div>
                  <i class="fa fa-chevron-right text-neutral-light"></i>
                </button>
                
                <button class="flex justify-between items-center w-full bg-white p-4 rounded-xl card-shadow card-hover">
                  <div class="flex items-center">
                    <div class="w-10 h-10 rounded-full bg-gray-100 flex items-center justify-center mr-3">
                      <i class="fa fa-file-text-o text-gray-600"></i>
                    </div>
                    <span>用户协议</span>
                  </div>
                  <i class="fa fa-chevron-right text-neutral-light"></i>
                </button>
                
                <button class="flex justify-between items-center w-full bg-white p-4 rounded-xl card-shadow card-hover">
                  <div class="flex items-center">
                    <div class="w-10 h-10 rounded-full bg-gray-100 flex items-center justify-center mr-3">
                      <i class="fa fa-star text-gray-600"></i>
                    </div>
                    <span>版本更新</span>
                  </div>
                  <span class="text-sm text-neutral-light">当前版本 1.2.0</span>
                </button>
              </div>
            </div>
          </div>
          
          <!-- 退出登录 -->
          <div class="mt-8">
            <button class="w-full py-3 text-danger font-medium border border-danger rounded-xl transition hover:bg-danger/5">
              <i class="fa fa-sign-out mr-2"></i> 退出登录
            </button>
          </div>
        </div>
        
        <!-- 底部导航 -->
        <div class="absolute bottom-0 left-0 right-0 bg-white border-t border-gray-100 py-2 px-4">
          <div class="grid grid-cols-4 gap-2">
            <button class="flex flex-col items-center text-neutral-light">
              <i class="fa fa-dashboard"></i>
              <span class="text-xs mt-1">仪表盘</span>
            </button>
            <button class="flex flex-col items-center text-neutral-light">
              <i class="fa fa-pie-chart"></i>
              <span class="text-xs mt-1">分析</span>
            </button>
            <button class="flex flex-col items-center text-neutral-light">
              <i class="fa fa-plus-circle text-2xl"></i>
              <span class="text-xs mt-1">记账</span>
            </button>
            <button class="flex flex-col items-center text-primary">
              <i class="fa fa-user-o"></i>
              <span class="text-xs mt-1">我的</span>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
  
  <script>
    // 初始化图表
    document.addEventListener('DOMContentLoaded', function() {
      // 仪表盘页面的收入支出图表
      const incomeExpenseCtx = document.getElementById('incomeExpenseChart').getContext('2d');
      new Chart(incomeExpenseCtx, {
        type: 'bar',
        data: {
          labels: ['1月', '2月', '3月', '4月', '5月', '6月'],
          datasets: [
            {
              label: '收入',
              data: [6500, 7200, 6800, 7500, 8000, 8450],
              backgroundColor: '#36D399',
              borderRadius: 4,
            },
            {
              label: '支出',
              data: [2800, 3200, 2900, 3100, 3000, 3280],
              backgroundColor: '#F87272',
              borderRadius: 4,
            }
          ]
        },
        options: {
          responsive: true,
          maintainAspectRatio: false,
          plugins: {
            legend: {
              position: 'top',
              labels: {
                boxWidth: 12,
                usePointStyle: true,
                pointStyle: 'circle'
              }
            }
          },
          scales: {
            y: {
              beginAtZero: true,
              grid: {
                display: true,
                color: 'rgba(0, 0, 0, 0.05)'
              }
            },
            x: {
              grid: {
                display: false
              }
            }
          }
        }
      });
      
      // 消费分析页面的支出分类图表
      const expenseCategoryCtx = document.getElementById('expenseCategoryChart').getContext('2d');
      new Chart(expenseCategoryCtx, {
        type: 'doughnut',
        data: {
          labels: ['餐饮', '购物', '住房', '交通', '其他'],
          datasets: [{
            data: [35, 25, 20, 15, 5],
            backgroundColor: [
              '#F87272',
              '#165DFF',
              '#9333EA',
              '#36D399',
              '#94A3B8'
            ],
            borderWidth: 0,
            cutout: '70%'
          }]
        },
        options: {
          responsive: true,
          maintainAspectRatio: false,
          plugins: {
            legend: {
              display: false
            }
          }
        }
      });
      
      // 消费分析页面的月度趋势图表
      const monthlyTrendCtx = document.getElementById('monthlyTrendChart').getContext('2d');
      new Chart(monthlyTrendCtx, {
        type: 'line',
        data: {
          labels: ['1月', '2月', '3月', '4月', '5月', '6月'],
          datasets: [{
            label: '收入',
            data: [6500, 7200, 6800, 7500, 8000, 8450],
            borderColor: '#36D399',
            backgroundColor: 'rgba(54, 211, 153, 0.1)',
            tension: 0.4,
            fill: true
          }]
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
              beginAtZero: true
              beginAtZero: true,
              grid: {
                display: true,
                color: 'rgba(0, 0, 0, 0.05)'
              }
            },
            x: {
              grid: {
                display: false
              }
            }
          }
        }
      });
    });
  </script>
</body>
</html>
