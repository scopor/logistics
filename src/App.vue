<template>
  <div class="min-h-screen bg-background text-foreground">
    <!-- 导航栏 -->
    <header
        class="border-b sticky top-0 bg-background/95 backdrop-blur supports-[backdrop-filter]:bg-background/60 z-50">
      <div class="container mx-auto px-4 py-4 flex justify-between items-center">
        <h1 class="text-2xl font-bold">粤宝物流供应链</h1>
        <nav>
          <ul class="flex space-x-4">
            <li><a href="#tracking" class="hover:text-primary">运单查询</a></li>
            <li><a href="#services" class="hover:text-primary">粤宝服务</a></li>
            <li><a href="#partners" class="hover:text-primary">合作伙伴</a></li>
            <li><a href="#testimonials" class="hover:text-primary">客户评价</a></li>
            <li><a href="#about" class="hover:text-primary">关于我们</a></li>
            <li><a href="#contact" class="hover:text-primary">联系我们</a></li>
          </ul>
        </nav>
      </div>
    </header>

    <!-- 英雄区域 -->
    <section class="relative py-40 bg-cover bg-center"
             style="background-image: url('//plus.unsplash.com/premium_photo-1661879449050-069f67e200bd?q=80&w=2622&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D');">
      <div class="absolute inset-0 bg-black bg-opacity-50"></div>
      <div class="container mx-auto px-4 text-center relative z-10 h-96">
        <h2 class="text-5xl font-bold mb-8 text-white">全国物流解决方案</h2>
        <p class="text-xl mb-8 text-white">快速、可靠、高效的货物运输服务</p>
        <p class="text-xl lg:mb-8 text-white text-start indent-10">
          粤宝供应链拥有在供应链及物流行业内经验丰富的资深专业团队，能为您在高档鞋服、直销行业、保健食品、日化用品等行业领域提供供应链战略及计划，物流服务等方面提供专业的咨询服务。</p>
        <p class="text-xl lg:mb-8 text-white text-start indent-10">
          通过对物流及供应链流程的优化，可帮助您降低库存，实现服务目标，提升客户服务水平，使得供应链适应和推动企业的发展。</p>
      </div>
    </section>

    <!-- 服务 -->
    <section id="services" class="py-20">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold mb-12 text-center">我们的服务</h2>
        <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
          <Card v-for="service in services" :key="service.title">
            <CardHeader>
              <CardTitle class="flex items-center">
                <component :is="service.icon" class="w-6 h-6 mr-2"/>
                {{ service.title }}
              </CardTitle>
            </CardHeader>
            <CardContent>
              <p>{{ service.description }}</p>
            </CardContent>
          </Card>
        </div>
      </div>
    </section>

    <!-- 特色 -->
    <section id="features" class="py-20 bg-muted">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold mb-12 text-center">为什么选择我们</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div v-for="feature in features" :key="feature.title" class="text-center">
            <div
                class="bg-primary text-primary-foreground rounded-full w-16 h-16 flex items-center justify-center mx-auto mb-4">
              <component :is="feature.icon" class="w-8 h-8"/>
            </div>
            <h3 class="text-xl font-semibold mb-2">{{ feature.title }}</h3>
            <p>{{ feature.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- 合作伙伴 -->
    <section id="partners" class="py-20">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold mb-12 text-center">我们的合作伙伴</h2>
        <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-8">
          <div v-for="partner in partners" :key="partner.name" class="flex items-center justify-center">
            <img :src="partner.logo" :alt="partner.name" class="max-h-16 max-w-full"/>
          </div>
        </div>
      </div>
    </section>

    <!-- 客户评价 -->
    <section id="testimonials" class="py-20">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold mb-12 text-center">客户评价</h2>
        <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
          <Card v-for="testimonial in testimonials" :key="testimonial.name">
            <CardContent class="pt-6">
              <div class="flex items-center mb-4">
                <div>
                  <h3 class="font-semibold">{{ testimonial.name }}</h3>
                  <p class="text-sm text-muted-foreground">{{ testimonial.company }}</p>
                </div>
              </div>
              <p class="italic">"{{ testimonial.quote }}"</p>
            </CardContent>
          </Card>
        </div>
      </div>
    </section>

    <!-- 关于我们 -->
    <section id="about" class="py-20">
      <div class="container mx-auto px-4">
        <div class="flex flex-col md:flex-row items-center">
          <div class="md:w-1/2 mb-8 md:mb-0">
            <img src="//upload.wikimedia.org/wikipedia/commons/6/6c/SVG_Simple_Icon.svg?height=400&width=600"
                 alt="About 粤宝" class=""/>
          </div>
          <div class="md:w-1/2 md:pl-12">
            <h2 class="text-3xl font-bold mb-6">关于 粤宝</h2>
            <p class="text-lg mb-4">
              粤宝 是一家领先的中国物流公司，拥有超过20年的行业经验。我们致力于为客户提供创新、可靠和高效的物流解决方案，满足他们不断变化的需求。
            </p>
            <p class="text-lg mb-4">
              我们的团队由行业专家组成，他们熟悉中国各地的物流挑战和机遇。无论您是小型企业还是大型跨国公司，我们都能为您量身定制最佳的物流策略。
            </p>
            <p>
              主要业务范围包括物流运输与配送、仓储管理、配送中心的规划与运营、供应链咨询及解决方案业务等。
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- 统计数据 -->
    <section class="py-20 bg-primary text-primary-foreground">
      <div class="container mx-auto px-4">
        <div class="grid grid-cols-2 md:grid-cols-4 gap-8 text-center">
          <div v-for="stat in stats" :key="stat.title">
            <div class="text-4xl font-bold mb-2">{{ stat.value }}</div>
            <div class="text-xl">{{ stat.title }}</div>
          </div>
        </div>
      </div>
    </section>

    <!-- 全国网络 -->
    <section class="py-20 bg-muted">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold mb-12 text-center">我们的全国网络</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center">
          <div class="relative">
            <div class="inset-0 bg-gradient-to-r from-primary/90 to-transparent rounded-lg flex items-center">
              <div class="p-8">
                <h3 class="text-2xl font-bold text-white mb-4">遍布全国的服务网络</h3>
                <p class="text-white mb-4">我们在全国超过 100+ 条线路处，为您提供无缝的物流服务。</p>
                <p class="text-white mb-4">我们在全国超过 30+ 个城市设有仓储服务，为您提供安全高效的货物进出管理服务。</p>
              </div>
            </div>
          </div>
          <div>
            <img src="https://www.gdybgyl.com/res/static/img/gyl3.jpg" alt="Company Locations" class="w-full"/>
          </div>
        </div>
      </div>
    </section>

    <!-- 运单查询 -->
    <section id="tracking" class="py-20">
      <div class="container">
        <h2 class="text-3xl font-bold mb-8 text-center">运单查询</h2>
        <div class="flex flex-col lg:flex-row lg:space-x-4">
          <div class="flex flex-col lg:w-1/3 w-full space-y-8">
            <Card class="h-40">
              <CardHeader>
                <CardTitle>输入您的运单号</CardTitle>
              </CardHeader>
              <CardContent>
                <form @submit.prevent="handleTracking" class="space-y-4">
                  <div class="flex space-x-2">
                    <Input v-model="trackingNumber" placeholder="请输入YBL开头的运单号" class="flex-grow"/>
                    <Button type="submit" :disabled="isLoading">
                      {{ isLoading ? '查询中...' : '查询' }}
                    </Button>
                  </div>
                </form>
              </CardContent>
            </Card>
            <div v-if="error" class="text-red-500 text-center">{{ error }}</div>
            <div v-if="trackingResult">
              <Card>
                <CardHeader>
                  <CardTitle>运单信息</CardTitle>
                </CardHeader>
                <CardContent>
                  <div class="space-y-2">
                    <p><strong>运单号：</strong>{{ trackingResult.orderid_chr }}</p>
                    <p><strong>创建时间：</strong>{{ trackingResult.createtime_dt }}</p>
                    <p><strong>创建人：</strong>{{ trackingResult.createname_vchr }}</p>
                    <p><strong>部门ID：</strong>{{ trackingResult.createdptid_vchr }}</p>
                  </div>
                </CardContent>
              </Card>
            </div>
          </div>
          <div v-if="trackingStatuses.length > 0" class="lg:w-2/3 w-full lg:mt-0 mt-8">
            <Card>
              <CardHeader>
                <CardTitle>运单状态</CardTitle>
              </CardHeader>
              <CardContent>
                <ul class="space-y-4">
                  <li v-for="status in trackingStatuses" :key="status.createtime_int"
                      class="border-b pb-4 last:border-b-0">
                    <p class="font-semibold">{{ status.createtime_int }}</p>
                    <p>{{ status.qus_vchr }}</p>
                    <p v-if="status.ans_vchr" class="text-sm text-gray-600">{{ status.ans_vchr }}</p>
                    <p class="text-sm text-gray-500">操作人: {{ status.oprator_vchr }}</p>
                  </li>
                </ul>
              </CardContent>
            </Card>
          </div>
        </div>
      </div>
    </section>

    <!-- 联系我们 -->
    <section id="contact" class="py-10">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold mb-12 text-center">联系我们</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div v-for="feature in contactUs" :key="feature.title" class="text-center">
            <div
                class="bg-primary text-primary-foreground rounded-full w-16 h-16 flex items-center justify-center mx-auto mb-4">
              <component :is="feature.icon" class="w-8 h-8"/>
            </div>
            <h3 class="text-xl font-semibold mb-2">{{ feature.title }}</h3>
            <p>{{ feature.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- 页脚 -->
    <footer class="bg-primary text-primary-foreground py-12">
      <div class="container mx-auto px-4">
        <div class="grid grid-cols-2 md:grid-cols-4 gap-8">
          <div>
            <h3 class="text-xl font-semibold mb-4">粤宝物流供应链</h3>
            <p>全国领先的物流解决方案提供商</p>
          </div>
          <div>
            <h4 class="font-semibold mb-4">快速链接</h4>
            <ul class="space-y-2">
              <li><a href="#" class="hover:underline">官网首页</a></li>
              <li><a href="#services" class="hover:underline">粤宝服务</a></li>
              <li><a href="#about" class="hover:underline">关于我们</a></li>
              <li><a href="#contact" class="hover:underline">联系我们</a></li>
            </ul>
          </div>
          <div>
            <h4 class="font-semibold mb-4">粤宝服务</h4>
            <ul class="space-y-2">
              <li><a href="#tracking" class="hover:underline">运单查询</a></li>
              <li><a href="#partners" class="hover:underline">合作伙伴</a></li>
              <li><a href="#testimonials" class="hover:underline">客户评价</a></li>
            </ul>
          </div>
          <div>
            <h4 class="font-semibold mb-4">关注我们</h4>
            <div class="w-28"><img src="https://www.gdybgyl.com/res/static/img/erweima.jpg" alt="二维码"/></div>
          </div>
        </div>
        <div class="mt-8 pt-8 border-t border-primary-foreground/20 text-center flex flex-col md:flex-row justify-center items-center">
            <span>2024 粤宝供应链. 保留所有权利。</span><span><a href="https://beian.miit.gov.cn/">备案号：粤ICP&nbsp;备2022072584号</a></span>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup lang="ts">
import {ref} from 'vue'
import axios from 'axios'
import {Button} from '@/components/ui/button'
import {Card, CardContent, CardHeader, CardTitle} from '@/components/ui/card'
import {Input} from '@/components/ui/input'
import {
  ClockIcon,
  FileTextIcon,
  GlobeIcon,
  Headphones,
  HeadphonesIcon,
  MailIcon,
  MapPinIcon,
  NetworkIcon,
  PhoneIcon,
  ShieldCheckIcon,
  TruckIcon,
  WarehouseIcon
} from 'lucide-vue-next'

const services = [
  {
    title: '精细仓储管理',
    description: '从收货入库到出仓，每一步都数字化记录，确保精细无误。',
    icon: TruckIcon
  },
  {
    title: '精准物流配送',
    description: '精耕门店配送、专柜配送、店店调拨、电商业务配送，我们更专业',
    icon: WarehouseIcon
  },
  {
    title: '供应链解决方案',
    description: '定制化的供应链解决方案，帮助您优化物流流程，提高运营效率，降低成本。',
    icon: NetworkIcon
  },
  {
    title: '货物运输服务',
    description: '为客户提供高性价比产品服务的综合型物流企业，致力于成为行业的领导者。',
    icon: FileTextIcon
  }
]

const features = [
  {
    title: '24/7 全天候服务',
    description: '我们的团队随时为您提供支持，确保您的物流需求得到及时满足。',
    icon: ClockIcon
  },
  {
    title: '全国网络',
    description: '遍布全国的服务网络，为您提供无缝的国内物流解决方案。',
    icon: GlobeIcon
  },
  {
    title: '安全可靠',
    description: '先进的跟踪系统和严格的安全措施，保障您的货物安全。',
    icon: ShieldCheckIcon
  },
  {
    title: '客户至上',
    description: '以客户需求为中心，提供个性化的服务和解决方案。',
    icon: HeadphonesIcon
  }
]

const contactUs = [
  {
    title: '公司位置',
    description: '广东省广州市白云区大源街道华邦物流园C栋六单元6405室',
    icon: MapPinIcon
  },
  {
    title: '座机',
    description: '020-29079033',
    icon: Headphones
  },
  {
    title: '手机',
    description: '+86 18588662388',
    icon: PhoneIcon
  },
  {
    title: '邮箱',
    description: 'hgx@gdybgyl.com',
    icon: MailIcon
  }
]

const stats = [
  {title: '服务城市', value: '100+'},
  {title: '满意客户', value: '10,000+'},
  {title: '准时交付率', value: '99.9%'},
  {title: '年运输量', value: '500万吨'}
]

const testimonials = [
  {
    name: '王经理',
    company: '某互联网智能家电公司',
    quote: '粤宝的服务让我们的供应链变得更加高效和可靠。他们的专业团队总是能够快速响应我们的需求。',
    avatar: ''
  },
  {
    name: '张经理',
    company: '某大型贸易有限公司',
    quote: '自从使用粤宝的仓储管理服务后，我们的库存周转率提高了 30%。他们的解决方案为我们节省了大量成本。',
    avatar: ''
  },
  {
    name: '谢先生',
    company: '某大型连锁超市',
    quote: '粤宝的货物运输服务安全可靠。他们帮助我们将产品安全、完好无缺的送达给客户。',
    avatar: ''
  },
  {
    name: '赵经理',
    company: '某一线知名食品集团',
    quote: '粤宝的冷链物流服务质量卓越。他们帮助我们将产品安全、新鲜地送达全国各地的客户手中。',
    avatar: ''
  }
]

const partners = [
  {name: '丹麦蓝罐', logo: 'https://www.kjeldsens.com/images/logo_b.jpg?height=60&width=120'},
  {name: 'Apollo', logo: 'https://www.gdybgyl.com/res/static/img/gyl6.png'},
  {name: '佳通轮胎', logo: 'https://www.giti.com/Portals/_default/skins/giticorptheme/images/general/logo.svg'},
  {
    name: '大润发',
    logo: 'https://www.rt-mart.com/static/frontEnd/assets/make-logo-mart-c6204b02d6ad3780374386cf26c603ec.png?height=60&width=120'
  },
  {name: '百果园', logo: 'http://p.cdn-static.cn/17830_17107420475172.png?imageView2/2/w/338/q/75'},
  {name: '卜蜂莲花', logo: 'http://www.cplotus.com/static/picture/menu_logo.png'},
  {name: '爱婴岛', logo: 'http://lm.baby.com.cn/images/LOGO.png'},
  {name: '中粮', logo: 'https://www.cofco.com/img/logo.png'},
  {name: '慕思', logo: 'https://www.gdybgyl.com/res/static/img/gyl12.jpg'},
  {name: '来利洪', logo: 'https://www.gdybgyl.com/res/static/img/gyl13.jpg'},
  {
    name: '斯林百兰',
    logo: 'https://mlbeit4pk4jr.i.optimole.com/cb:VzzP.68a0/w:auto/h:auto/q:mauto/ig:avif/f:best/https://i0.wp.com/www.slumberland.com.hk/wp-content/uploads/2020/07/slumberland_logo_big.png?fit=167%2C87&ssl=1'
  },
  {name: '德蒙斯特', logo: 'https://www.gdybgyl.com/res/static/img/gyl16.jpg'}
]

interface TrackingResult {
  orderid_chr: string;
  createtime_dt: string;
  createname_vchr: string;
  createdptid_vchr: string;
}

interface TrackingStatus {
  orderid_chr: string;
  createtime_int: string;
  qus_vchr: string;
  ans_vchr: string;
  oprator_vchr: string;
}

interface ApiResponse {
  status: number;
  msg: string;
  result: [TrackingResult[], TrackingStatus[]];
}

const trackingNumber = ref('')
const trackingResult = ref<TrackingResult | null>(null)
const trackingStatuses = ref<TrackingStatus[]>([])
const isLoading = ref(false)
const error = ref<string | null>(null)

const handleTracking = async () => {
  isLoading.value = true
  error.value = null
  trackingResult.value = null
  trackingStatuses.value = []

  try {
    const response = await axios.post<ApiResponse>('https://www.gdybgyl.com:7002/public/openApi', {
      opration: "search_order",
      type: "orderid",
      key: trackingNumber.value
    })

    if (response.data.status === 200 && response.data.result.length === 2) {
      trackingResult.value = response.data.result[0][0]
      trackingStatuses.value = response.data.result[1]
      if (!response.data.result[0].length) {
        error.value = '未找到运单信息，请确认是否填写正确。'
      }
    } else {
      error.value = '未找到运单信息，请确认是否填写正确。'
    }
  } catch (err) {
    error.value = '查询失败，请稍后再试。'
    console.error('Error fetching tracking info:', err)
  } finally {
    isLoading.value = false
  }
}
</script>
