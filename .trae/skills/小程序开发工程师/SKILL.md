---
name: "小程序开发工程师"
description: "专门开发微信小程序，负责页面开发、组件封装、微信能力集成、性能优化、分包加载等功能开发。Invoke when user needs to develop WeChat mini program features, implement WeChat API integration, optimize performance, or configure subpackages."
---

# 小程序开发工程师

> 版本：v2.0 | 日期：2026-04-07 | 工作流节点：Assemble
> 核心理念：Superpowers 四原则（TDD、系统性、简化、证据）

## 角色定位

负责微信小程序的核心功能开发，包括：
- 页面开发与组件封装
- 微信能力集成（登录、支付、分享等）
- 状态管理实现
- 性能优化与分包加载
- 数据缓存策略
- 微信审核规范遵循

**Superpowers 技能标注：**
- **TDD 开发者**：每个页面/组件/工具函数均采用测试驱动开发（miniprogram-simulate）
- **系统化调试者**：遵循4步调试法快速定位问题
- **子代理协调者**：可拆分子任务并行开发（页面层/组件层/工具层）

## Superpowers 技能

```
┌─────────────────────────────────────────────────────────────┐
│        小程序开发工程师 Superpowers 技能树                    │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  【核心开发技能】                                            │
│  ├── test-driven-development     测试驱动开发(miniprogram-   │
│  │                              simulate)                   │
│  ├── systematic-debugging        系统化调试(4步法)           │
│  ├── subagent-driven-development 子代理并行开发              │
│  └── verification-before-completion 完成前验证               │
│                                                             │
│  【小程序专项技能】                                          │
│  ├── miniprogram-page-dev       小程序页面开发(TDD)         │
│  ├── miniprogram-component-dev  小程序组件封装(TDD)         │
│  ├── wechat-api-integration     微信API集成                 │
│  ├── miniprogram-subpackage     分包加载优化                 │
│  └── miniprogram-perf           小程序性能优化               │
│                                                             │
│  【协作技能】                                                │
│  └── requesting-code-review      代码审查                   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### ⚡ test-driven-development（测试驱动开发）

小程序 TDD 使用 `miniprogram-simulate` 框架进行单元测试，开发流程：

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📱 小程序 - TDD 开发模式
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Step 1: RED - 编写失败的测试用例
┌─────────────────────────────────────────────┐
// tests/components/product-card.test.js
describe('product-card', () => {
    it('should render product name correctly', () => { ... });
    it('should trigger buy event when button clicked', () => { ... });
});
└─────────────────────────────────────────────
→ 运行 npm test → ❌ 失败

Step 2: GREEN - 编写最少实现
┌─────────────────────────────────────────────
// components/product-card/product-card.js
Component({ ... });
└─────────────────────────────────────────────
→ 运行 npm test → ✅ 通过

Step 3: REFACTOR - 重构优化
├── 提取公共逻辑
├── 优化渲染性能
└── 运行 npm test → ✅ 全部通过

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### ⚡ systematic-debugging（系统化调试）

4步调试法，适用于小程序全场景：

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔍 小程序 - 系统化调试 4 步法
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Step 1: 问题表征（精确描述问题）
├── 复现步骤是什么？
├── 预期结果 vs 实际结果？
├── 出现频率？（必现 / 偶现 / 特定机型）
└── 是否在真机和模拟器表现一致？

Step 2: 假设生成（列出可能原因）
├── 数据层：API返回数据异常？缓存脏数据？
├── 逻辑层：setData时机不对？生命周期顺序问题？
├── 视图层：WXML渲染条件错误？样式覆盖？
├── 环境层：基础库版本？网络环境？权限配置？
└── 兼容层：iOS/Android 差异？不同机型差异？

Step 3: 假设验证（逐一排除）
├── vConsole 检查网络请求和数据流
├── AppData 面板检查状态变化
├── 断点调试关键逻辑
├── 对比真机 vs 模拟器行为
└── 二分法注释代码定位

Step 4: 根因定位与修复
├── 确认根因
├── 编写修复代码
├── 补充测试用例防止回归
└── 验证修复效果

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### ⚡ subagent-driven-development（子代理并行开发）

将小程序开发任务拆分为可并行的子任务：

```
主代理协调者
    │
    ├── 子代理 A: 页面层开发
    │   ├── pages/index/（TDD）
    │   ├── pages/category/（TDD）
    │   └── pages/cart/（TDD）
    │
    ├── 子代理 B: 组件层开发
    │   ├── components/product-card/（TDD）
    │   ├── components/search-bar/（TDD）
    │   └── components/empty-state/（TDD）
    │
    ├── 子代理 C: 工具层开发
    │   ├── utils/wechat.js（TDD）
    │   ├── services/request.js（TDD）
    │   └── stores/（TDD）
    │
    └── 子代理 D: 联调测试（等 A、B、C 完成）
        ├── 集成测试
        └── 真机验证
```

### ⚡ verification-before-completion（完成前验证）

每个功能完成前必须通过的验证清单：

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ 完成前验证清单
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

代码质量验证：
  ├── npm test 全部通过？
  ├── ESLint 检查通过？
  ├── 代码审查无 Critical 问题？
  └── 无 console.log 残留？

功能验证：
  ├── 微信开发者工具运行正常？
  ├── 真机测试通过？（iOS + Android）
  ├── 微信能力集成正常？（登录/支付/分享）
  └── 分包加载正常？

性能验证：
  ├── 包体积 < 2MB（主包 < 1.5MB）？
  ├── 首屏渲染 < 1.5s？
  ├── setData 数据量合理？
  └── 图片懒加载生效？

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

## 技术栈

```
框架选择：原生微信小程序 / Taro 3.x / uni-app
状态管理：MobX-Miniprogram / Redux / Vuex
UI组件：Vant Weapp / Taro UI / uView
样式方案：WXSS / SCSS / Less
构建工具：微信开发者工具 / Webpack
云开发：微信云开发 / 自有后端

【Superpowers 新增】
测试框架：miniprogram-simulate + Jest
代码检查：ESLint + Prettier
覆盖率：Jest --coverage（目标 > 80%）
调试工具：vConsole + 微信开发者工具
```

## 触发条件

**关键词：**
- "开发"、"实现"、"编码"
- "小程序"、"页面"、"组件"
- "微信登录"、"微信支付"、"分享"
- "分包"、"优化"、"缓存"
- "测试"、"调试"、"真机"

**场景：**
- 需要开发小程序功能
- 需要集成微信能力
- 需要性能优化
- 需要分包加载配置
- 需要封装组件
- 需要编写小程序测试用例

## 核心能力

### 1. 页面开发

```javascript
// pages/index/index.js
Page({
  data: {
    userInfo: null,
    list: [],
    loading: false,
    hasMore: true
  },

  onLoad(options) {
    this.loadData();
  },

  onShow() {
    // 页面显示
  },

  onPullDownRefresh() {
    this.refreshData();
  },

  onReachBottom() {
    this.loadMore();
  },

  onShareAppMessage() {
    return {
      title: '分享标题',
      path: '/pages/index/index?id=123'
    };
  },

  async loadData() {
    this.setData({ loading: true });
    try {
      const res = await api.getList();
      this.setData({
        list: res.data,
        loading: false
      });
    } catch (error) {
      this.setData({ loading: false });
      wx.showToast({ title: '加载失败', icon: 'none' });
    }
  },

  handleTap(e) {
    const { id } = e.currentTarget.dataset;
    wx.navigateTo({
      url: `/pages/detail/detail?id=${id}`
    });
  }
});
```

```xml
<!-- pages/index/index.wxml -->
<view class="container">
  <view class="header">
    <text class="title">首页</text>
  </view>
  
  <scroll-view 
    class="content" 
    scroll-y 
    refresher-enabled
    bindrefresherrefresh="onPullDownRefresh"
    bindscrolltolower="onReachBottom"
  >
    <view 
      class="item" 
      wx:for="{{list}}" 
      wx:key="id"
      data-id="{{item.id}}"
      bindtap="handleTap"
    >
      <image class="item-image" src="{{item.image}}" mode="aspectFill" lazy-load />
      <view class="item-info">
        <text class="item-title">{{item.title}}</text>
        <text class="item-desc">{{item.description}}</text>
      </view>
    </view>
    
    <view class="loading" wx:if="{{loading}}">
      <text>加载中...</text>
    </view>
  </scroll-view>
</view>
```

### 2. 组件封装

```javascript
// components/product-card/product-card.js
Component({
  properties: {
    product: {
      type: Object,
      value: {}
    },
    showPrice: {
      type: Boolean,
      value: true
    }
  },

  data: {
    // 内部数据
  },

  lifetimes: {
    attached() {
      // 组件挂载
    },
    detached() {
      // 组件卸载
    }
  },

  methods: {
    handleBuy(e) {
      const { product } = this.data;
      this.triggerEvent('buy', { product });
    },

    handleDetail(e) {
      const { product } = this.data;
      this.triggerEvent('detail', { product });
    }
  }
});
```

```xml
<!-- components/product-card/product-card.wxml -->
<view class="product-card" bindtap="handleDetail">
  <image class="product-image" src="{{product.image}}" mode="aspectFill" lazy-load />
  <view class="product-info">
    <text class="product-name">{{product.name}}</text>
    <text class="product-desc" wx:if="{{product.description}}">{{product.description}}</text>
    <view class="product-footer">
      <text class="product-price" wx:if="{{showPrice}}">¥{{product.price}}</text>
      <button 
        class="buy-btn" 
        size="mini" 
        type="primary"
        catchtap="handleBuy"
      >购买</button>
    </view>
  </view>
</view>
```

### 3. 微信能力集成

```javascript
// utils/wechat.js

/**
 * 微信登录
 */
const wxLogin = () => {
  return new Promise((resolve, reject) => {
    wx.login({
      success: (res) => {
        if (res.code) {
          resolve(res.code);
        } else {
          reject(new Error('登录失败'));
        }
      },
      fail: reject
    });
  });
};

/**
 * 获取用户信息
 */
const getUserProfile = () => {
  return new Promise((resolve, reject) => {
    wx.getUserProfile({
      desc: '用于完善用户资料',
      success: resolve,
      fail: reject
    });
  });
};

/**
 * 微信支付
 */
const wxPay = (payment) => {
  return new Promise((resolve, reject) => {
    wx.requestPayment({
      timeStamp: payment.timeStamp,
      nonceStr: payment.nonceStr,
      package: payment.package,
      signType: payment.signType,
      paySign: payment.paySign,
      success: resolve,
      fail: reject
    });
  });
};

/**
 * 选择图片
 */
const chooseImage = (count = 1, sourceType = ['album', 'camera']) => {
  return new Promise((resolve, reject) => {
    wx.chooseMedia({
      count,
      mediaType: ['image'],
      sourceType,
      success: resolve,
      fail: reject
    });
  });
};

/**
 * 上传文件
 */
const uploadFile = (filePath, url) => {
  return new Promise((resolve, reject) => {
    wx.uploadFile({
      url,
      filePath,
      name: 'file',
      success: resolve,
      fail: reject
    });
  });
};

/**
 * 获取位置
 */
const getLocation = (type = 'wgs84') => {
  return new Promise((resolve, reject) => {
    wx.getLocation({
      type,
      success: resolve,
      fail: reject
    });
  });
};

/**
 * 扫码
 */
const scanCode = () => {
  return new Promise((resolve, reject) => {
    wx.scanCode({
      success: resolve,
      fail: reject
    });
  });
};

module.exports = {
  wxLogin,
  getUserProfile,
  wxPay,
  chooseImage,
  uploadFile,
  getLocation,
  scanCode
};
```

### 4. 网络请求封装

```javascript
// services/request.js

const BASE_URL = 'https://api.example.com';
const TIMEOUT = 10000;

// 请求拦截
const requestInterceptor = (options) => {
  const token = wx.getStorageSync('token');
  if (token) {
    options.header = {
      ...options.header,
      'Authorization': `Bearer ${token}`
    };
  }
  return options;
};

// 响应拦截
const responseInterceptor = (response) => {
  if (response.statusCode === 401) {
    // Token过期，清除登录状态
    wx.removeStorageSync('token');
    wx.removeStorageSync('userInfo');
    wx.navigateTo({ url: '/pages/login/login' });
    throw new Error('登录已过期');
  }
  
  if (response.statusCode !== 200) {
    throw new Error(response.data.message || '请求失败');
  }
  
  return response.data;
};

/**
 * 通用请求方法
 */
const request = (options) => {
  return new Promise((resolve, reject) => {
    // 请求拦截
    options = requestInterceptor(options);
    
    wx.request({
      url: `${BASE_URL}${options.url}`,
      method: options.method || 'GET',
      data: options.data,
      header: {
        'Content-Type': 'application/json',
        ...options.header
      },
      timeout: TIMEOUT,
      success: (res) => {
        try {
          const data = responseInterceptor(res);
          resolve(data);
        } catch (error) {
          reject(error);
        }
      },
      fail: (err) => {
        reject(new Error('网络请求失败，请检查网络'));
      }
    });
  });
};

// API封装
const api = {
  // 用户相关
  login: (code) => request({ url: '/auth/login', method: 'POST', data: { code } }),
  getUserInfo: () => request({ url: '/user/info' }),
  updateUserInfo: (data) => request({ url: '/user/info', method: 'PUT', data }),
  
  // 商品相关
  getProductList: (params) => request({ url: '/products', data: params }),
  getProductDetail: (id) => request({ url: `/products/${id}` }),
  
  // 订单相关
  createOrder: (data) => request({ url: '/orders', method: 'POST', data }),
  getOrderList: (params) => request({ url: '/orders', data: params }),
  getOrderDetail: (id) => request({ url: `/orders/${id}` }),
  
  // 支付相关
  createPayment: (orderId) => request({ url: '/payment/create', method: 'POST', data: { orderId } })
};

module.exports = { request, api };
```

### 5. 状态管理（MobX）

```javascript
// stores/userStore.js
import { observable, action } from 'mobx-miniprogram';

export const userStore = observable({
  // 数据
  userInfo: null,
  isLogin: false,
  permissions: [],

  // 计算属性
  get userName() {
    return this.userInfo ? this.userInfo.nickName : '';
  },

  get avatarUrl() {
    return this.userInfo ? this.userInfo.avatarUrl : '';
  },

  get hasPermission() {
    return (permission) => this.permissions.includes(permission);
  },

  // Actions
  setUserInfo: action(function(info) {
    this.userInfo = info;
    this.isLogin = true;
    wx.setStorageSync('userInfo', info);
  }),

  setPermissions: action(function(permissions) {
    this.permissions = permissions;
    wx.setStorageSync('permissions', permissions);
  }),

  logout: action(function() {
    this.userInfo = null;
    this.isLogin = false;
    this.permissions = [];
    wx.removeStorageSync('userInfo');
    wx.removeStorageSync('token');
    wx.removeStorageSync('permissions');
  }),

  // 初始化
  init: action(function() {
    const userInfo = wx.getStorageSync('userInfo');
    const permissions = wx.getStorageSync('permissions');
    if (userInfo) {
      this.userInfo = userInfo;
      this.isLogin = true;
    }
    if (permissions) {
      this.permissions = permissions;
    }
  })
});
```

```javascript
// stores/cartStore.js
import { observable, action } from 'mobx-miniprogram';

export const cartStore = observable({
  // 数据
  items: [],
  selectedIds: [],

  // 计算属性
  get totalCount() {
    return this.items.reduce((sum, item) => sum + item.count, 0);
  },

  get totalPrice() {
    return this.items
      .filter(item => this.selectedIds.includes(item.id))
      .reduce((sum, item) => sum + item.price * item.count, 0);
  },

  get selectedItems() {
    return this.items.filter(item => this.selectedIds.includes(item.id));
  },

  get isAllSelected() {
    return this.items.length > 0 && this.selectedIds.length === this.items.length;
  },

  // Actions
  addItem: action(function(product) {
    const existingItem = this.items.find(item => item.id === product.id);
    if (existingItem) {
      existingItem.count += 1;
    } else {
      this.items.push({ ...product, count: 1 });
    }
    this.saveToStorage();
  }),

  removeItem: action(function(productId) {
    this.items = this.items.filter(item => item.id !== productId);
    this.selectedIds = this.selectedIds.filter(id => id !== productId);
    this.saveToStorage();
  }),

  updateCount: action(function(productId, count) {
    const item = this.items.find(item => item.id === productId);
    if (item) {
      item.count = count;
      if (count <= 0) {
        this.removeItem(productId);
      } else {
        this.saveToStorage();
      }
    }
  }),

  toggleSelect: action(function(productId) {
    const index = this.selectedIds.indexOf(productId);
    if (index > -1) {
      this.selectedIds.splice(index, 1);
    } else {
      this.selectedIds.push(productId);
    }
    this.saveToStorage();
  }),

  toggleSelectAll: action(function() {
    if (this.isAllSelected) {
      this.selectedIds = [];
    } else {
      this.selectedIds = this.items.map(item => item.id);
    }
    this.saveToStorage();
  }),

  clear: action(function() {
    this.items = [];
    this.selectedIds = [];
    this.saveToStorage();
  }),

  saveToStorage: action(function() {
    wx.setStorageSync('cart', {
      items: this.items,
      selectedIds: this.selectedIds
    });
  }),

  init: action(function() {
    const cart = wx.getStorageSync('cart');
    if (cart) {
      this.items = cart.items || [];
      this.selectedIds = cart.selectedIds || [];
    }
  })
});
```

### 6. 分包加载配置

```json
// app.json
{
  "pages": [
    "pages/index/index",
    "pages/category/category",
    "pages/cart/cart",
    "pages/mine/mine"
  ],
  "subpackages": [
    {
      "root": "package-order",
      "name": "order",
      "pages": [
        "pages/confirm/confirm",
        "pages/payment/payment",
        "pages/result/result",
        "pages/list/list",
        "pages/detail/detail"
      ]
    },
    {
      "root": "package-product",
      "name": "product",
      "pages": [
        "pages/detail/detail",
        "pages/search/search",
        "pages/filter/filter"
      ]
    },
    {
      "root": "package-user",
      "name": "user",
      "pages": [
        "pages/settings/settings",
        "pages/address/list/list",
        "pages/address/edit/edit",
        "pages/coupon/coupon"
      ]
    }
  ],
  "preloadRule": {
    "pages/cart/cart": {
      "network": "all",
      "packages": ["package-order"]
    },
    "pages/category/category": {
      "network": "all",
      "packages": ["package-product"]
    }
  },
  "tabBar": {
    "list": [
      { "pagePath": "pages/index/index", "text": "首页" },
      { "pagePath": "pages/category/category", "text": "分类" },
      { "pagePath": "pages/cart/cart", "text": "购物车" },
      { "pagePath": "pages/mine/mine", "text": "我的" }
    ]
  }
}
```

### 7. 性能优化

```javascript
// utils/optimize.js

/**
 * 图片懒加载优化
 */
const optimizeImage = (url, width, height) => {
  // 使用七牛云/阿里OSS图片处理
  return `${url}?imageView2/1/w/${width}/h/${height}/q/80`;
};

/**
 * 列表项高度固定（用于virtual-list）
 */
const ITEM_HEIGHT = 100;

/**
 * 防抖函数
 */
const debounce = (fn, delay = 300) => {
  let timer = null;
  return function(...args) {
    if (timer) clearTimeout(timer);
    timer = setTimeout(() => {
      fn.apply(this, args);
    }, delay);
  };
};

/**
 * 节流函数
 */
const throttle = (fn, interval = 300) => {
  let lastTime = 0;
  return function(...args) {
    const now = Date.now();
    if (now - lastTime >= interval) {
      lastTime = now;
      fn.apply(this, args);
    }
  };
};

/**
 * 数据缓存
 */
const cache = {
  set(key, data, expire = 3600) {
    wx.setStorageSync(key, {
      data,
      expire: Date.now() + expire * 1000
    });
  },
  get(key) {
    const cached = wx.getStorageSync(key);
    if (cached && cached.expire > Date.now()) {
      return cached.data;
    }
    wx.removeStorageSync(key);
    return null;
  }
};

module.exports = {
  optimizeImage,
  debounce,
  throttle,
  cache
};
```

## TDD 代码示例（小程序专项）

### 组件单元测试

```javascript
// tests/components/product-card.test.js
const simulate = require('miniprogram-simulate');
const path = require('path');

describe('product-card', () => {
  let component;

  const mockProduct = {
    id: '001',
    name: '测试商品',
    description: '这是一个测试商品',
    image: 'https://example.com/product.jpg',
    price: 99.9
  };

  beforeEach(() => {
    component = simulate.render(
      require(path.resolve(__dirname, '../../components/product-card/product-card')),
      {
        product: mockProduct,
        showPrice: true
      }
    );
    component.attach(document.createElement('parent'));
  });

  afterEach(() => {
    component && component.detach();
  });

  it('should render product name correctly', () => {
    const nameEl = component.querySelector('.product-name');
    expect(nameEl.dom.textContent).toBe('测试商品');
  });

  it('should render product price when showPrice is true', () => {
    const priceEl = component.querySelector('.product-price');
    expect(priceEl.dom.textContent).toContain('99.9');
  });

  it('should not render price when showPrice is false', () => {
    const comp = simulate.render(
      require(path.resolve(__dirname, '../../components/product-card/product-card')),
      {
        product: mockProduct,
        showPrice: false
      }
    );
    comp.attach(document.createElement('parent'));
    const priceEl = comp.querySelector('.product-price');
    expect(priceEl).toBeNull();
    comp.detach();
  });

  it('should render product description', () => {
    const descEl = component.querySelector('.product-desc');
    expect(descEl.dom.textContent).toBe('这是一个测试商品');
  });

  it('should trigger detail event when card is tapped', () => {
    const spy = jest.fn();
    component.addEventListener('detail', spy);
    const cardEl = component.querySelector('.product-card');
    cardEl.dispatchEvent('tap');
    expect(spy).toHaveBeenCalled();
    expect(spy.mock.calls[0][0].detail.product.id).toBe('001');
  });

  it('should trigger buy event when buy button is clicked', () => {
    const spy = jest.fn();
    component.addEventListener('buy', spy);
    const buyBtn = component.querySelector('.buy-btn');
    buyBtn.dispatchEvent('tap');
    expect(spy).toHaveBeenCalled();
    expect(spy.mock.calls[0][0].detail.product.name).toBe('测试商品');
  });

  it('should not render description when product has no description', () => {
    const noDescProduct = { ...mockProduct, description: '' };
    const comp = simulate.render(
      require(path.resolve(__dirname, '../../components/product-card/product-card')),
      { product: noDescProduct, showPrice: true }
    );
    comp.attach(document.createElement('parent'));
    const descEl = comp.querySelector('.product-desc');
    expect(descEl).toBeNull();
    comp.detach();
  });
});
```

### 页面单元测试

```javascript
// tests/pages/index.test.js
const simulate = require('miniprogram-simulate');
const path = require('path');

describe('pages/index', () => {
  let page;

  beforeEach(() => {
    page = simulate.render(
      require(path.resolve(__dirname, '../../pages/index/index'))
    );
    page.attach(document.createElement('parent'));
  });

  afterEach(() => {
    page && page.detach();
  });

  it('should have initial data state', () => {
    const data = page.data;
    expect(data.userInfo).toBeNull();
    expect(data.list).toEqual([]);
    expect(data.loading).toBe(false);
    expect(data.hasMore).toBe(true);
  });

  it('should render header title', () => {
    const titleEl = page.querySelector('.title');
    expect(titleEl.dom.textContent).toBe('首页');
  });

  it('should show loading text when loading is true', async () => {
    page.setData({ loading: true });
    await simulate.sleep(0);
    const loadingEl = page.querySelector('.loading');
    expect(loadingEl.dom.textContent).toContain('加载中');
  });

  it('should render list items correctly', async () => {
    const mockList = [
      { id: '1', title: '商品1', description: '描述1', image: 'https://example.com/1.jpg' },
      { id: '2', title: '商品2', description: '描述2', image: 'https://example.com/2.jpg' }
    ];
    page.setData({ list: mockList });
    await simulate.sleep(0);
    const items = page.querySelectorAll('.item');
    expect(items.length).toBe(2);
  });

  it('should handle tap event on list item', () => {
    const spy = jest.fn();
    wx.navigateTo = spy;
    const mockList = [
      { id: '123', title: '商品1', description: '描述1', image: 'https://example.com/1.jpg' }
    ];
    page.setData({ list: mockList });
    const itemEl = page.querySelector('.item');
    itemEl.dispatchEvent('tap');
    expect(spy).toHaveBeenCalledWith({
      url: '/pages/detail/detail?id=123'
    });
  });

  it('should not render items when list is empty', () => {
    const items = page.querySelectorAll('.item');
    expect(items.length).toBe(0);
  });
});
```

### 工具函数单元测试

```javascript
// tests/utils/optimize.test.js
const { debounce, throttle, cache, optimizeImage } = require('../../utils/optimize');

describe('utils/optimize', () => {
  describe('debounce', () => {
    jest.useFakeTimers();

    it('should delay function execution', () => {
      const fn = jest.fn();
      const debounced = debounce(fn, 300);
      debounced();
      expect(fn).not.toHaveBeenCalled();
      jest.advanceTimersByTime(300);
      expect(fn).toHaveBeenCalledTimes(1);
    });

    it('should cancel previous call when called again within delay', () => {
      const fn = jest.fn();
      const debounced = debounce(fn, 300);
      debounced();
      debounced();
      debounced();
      jest.advanceTimersByTime(300);
      expect(fn).toHaveBeenCalledTimes(1);
    });
  });

  describe('throttle', () => {
    jest.useFakeTimers();

    it('should execute function immediately on first call', () => {
      const fn = jest.fn();
      const throttled = throttle(fn, 300);
      throttled();
      expect(fn).toHaveBeenCalledTimes(1);
    });

    it('should not execute again within interval', () => {
      const fn = jest.fn();
      const throttled = throttle(fn, 300);
      throttled();
      throttled();
      throttled();
      expect(fn).toHaveBeenCalledTimes(1);
      jest.advanceTimersByTime(300);
      throttled();
      expect(fn).toHaveBeenCalledTimes(2);
    });
  });

  describe('cache', () => {
    it('should store and retrieve data', () => {
      cache.set('test_key', { name: 'test' });
      const result = cache.get('test_key');
      expect(result).toEqual({ name: 'test' });
    });

    it('should return null for expired cache', () => {
      cache.set('expire_key', 'data', -1);
      const result = cache.get('expire_key');
      expect(result).toBeNull();
    });

    it('should return null for non-existent key', () => {
      const result = cache.get('non_existent');
      expect(result).toBeNull();
    });
  });

  describe('optimizeImage', () => {
    it('should append image processing parameters', () => {
      const url = 'https://example.com/image.jpg';
      const result = optimizeImage(url, 200, 200);
      expect(result).toContain('imageView2/1/w/200/h/200/q/80');
    });
  });
});
```

### 网络请求单元测试

```javascript
// tests/services/request.test.js

describe('services/request', () => {
  let request;
  let api;

  beforeEach(() => {
    jest.resetModules();
    jest.spyOn(wx, 'getStorageSync').mockReturnValue('test_token');
    jest.spyOn(wx, 'removeStorageSync').mockImplementation(() => {});
    jest.spyOn(wx, 'navigateTo').mockImplementation(() => {});
    const module = require('../../services/request');
    request = module.request;
    api = module.api;
  });

  afterEach(() => {
    jest.restoreAllMocks();
  });

  it('should add authorization header when token exists', async () => {
    wx.request = jest.fn(({ header, success }) => {
      success({ statusCode: 200, data: { success: true } });
    });

    await request({ url: '/user/info' });

    expect(wx.request).toHaveBeenCalledWith(
      expect.objectContaining({
        header: expect.objectContaining({
          'Authorization': 'Bearer test_token'
        })
      })
    );
  });

  it('should handle 401 response and redirect to login', async () => {
    wx.request = jest.fn(({ success }) => {
      success({ statusCode: 401, data: { message: 'Unauthorized' } });
    });

    await expect(request({ url: '/user/info' })).rejects.toThrow('登录已过期');
    expect(wx.removeStorageSync).toHaveBeenCalledWith('token');
    expect(wx.removeStorageSync).toHaveBeenCalledWith('userInfo');
    expect(wx.navigateTo).toHaveBeenCalledWith({ url: '/pages/login/login' });
  });

  it('should reject on non-200 status code', async () => {
    wx.request = jest.fn(({ success }) => {
      success({ statusCode: 500, data: { message: '服务器错误' } });
    });

    await expect(request({ url: '/test' })).rejects.toThrow('服务器错误');
  });

  it('should reject on network failure', async () => {
    wx.request = jest.fn(({ fail }) => {
      fail(new Error('Network Error'));
    });

    await expect(request({ url: '/test' })).rejects.toThrow('网络请求失败');
  });

  it('should return data on successful request', async () => {
    const mockData = { id: 1, name: 'test' };
    wx.request = jest.fn(({ success }) => {
      success({ statusCode: 200, data: mockData });
    });

    const result = await request({ url: '/test' });
    expect(result).toEqual(mockData);
  });

  describe('api methods', () => {
    beforeEach(() => {
      wx.request = jest.fn(({ success }) => {
        success({ statusCode: 200, data: { success: true } });
      });
    });

    it('api.login should call with correct params', async () => {
      await api.login('test_code');
      expect(wx.request).toHaveBeenCalledWith(
        expect.objectContaining({
          url: expect.stringContaining('/auth/login'),
          method: 'POST',
          data: { code: 'test_code' }
        })
      );
    });

    it('api.getProductList should pass query params', async () => {
      await api.getProductList({ page: 1, size: 10 });
      expect(wx.request).toHaveBeenCalledWith(
        expect.objectContaining({
          url: expect.stringContaining('/products'),
          data: { page: 1, size: 10 }
        })
      );
    });

    it('api.createOrder should use POST method', async () => {
      await api.createOrder({ productId: '001', quantity: 2 });
      expect(wx.request).toHaveBeenCalledWith(
        expect.objectContaining({
          url: expect.stringContaining('/orders'),
          method: 'POST'
        })
      );
    });
  });
});
```

## 系统化调试

### 真机调试

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📱 小程序真机调试要点
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

调试前准备：
  ├── 确保手机和电脑在同一网络
  ├── 微信版本 >= 7.0.0
  ├── 基础库版本与项目配置一致
  └── 开启开发者模式（Android）

真机调试 vs 模拟器差异：
  ├── iOS/Android 渲染差异（CSS兼容）
  ├── 真机性能更接近用户实际体验
  ├── 部分API真机才能使用（扫码、支付等）
  ├── 真机网络环境更复杂（弱网、切换）
  └── 真机内存限制更严格

真机调试步骤：
  Step 1: 微信开发者工具 → 真机调试
  Step 2: 扫码连接手机
  Step 3: 打开 vConsole 查看日志
  Step 4: 复现问题，收集信息
  Step 5: 结合系统化4步法定位根因

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### vConsole 使用

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔧 vConsole 调试面板
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

开启方式：
  ├── 开发版/体验版：自动开启
  └── 正式版：需通过特定入口开启

常用面板：
  ├── Log: 查看console输出
  ├── System: 查看系统信息（基础库版本、UA等）
  ├── Network: 查看网络请求（Header、Body、耗时）
  ├── Element: 查看DOM结构（类似Chrome DevTools）
  ├── Storage: 查看/编辑本地存储
  └── AppData: 查看Page/Component的data状态

调试技巧：
  ├── 使用 console.group() 分组日志
  ├── 使用 console.table() 查看数组/对象
  ├── 使用 console.time() / console.timeEnd() 计时
  ├── 使用 console.trace() 追踪调用栈
  └── 关键节点打日志（setData前后、API调用前后）
```

### 网络问题调试

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🌐 网络问题调试指南
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

常见问题：
  ├── 请求超时 → 检查网络环境 + TIMEOUT配置
  ├── 401未授权 → 检查token有效性 + 刷新机制
  ├── 域名不合法 → 检查request合法域名配置
  ├── SSL证书问题 → 检查HTTPS证书配置
  ├── DNS解析失败 → 检查域名 + CDN配置
  └── 数据格式错误 → 检查Content-Type + 序列化

调试方法：
  Step 1: vConsole Network面板查看请求详情
  Step 2: 对比Request Header和Response Header
  Step 3: 检查请求参数是否正确
  Step 4: 检查响应数据格式
  Step 5: 弱网环境模拟（开发者工具→网络→自定义）
```

### 性能分析

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
⚡ 性能分析工具与方法
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

微信开发者工具 Audits 面板：
  ├── 首次渲染耗时分析
  ├── setData 调用频率和数据量
  ├── WXML 节点数量
  ├── 图片资源加载情况
  └── 脚本执行耗时

Performance 面板：
  ├── 脚本执行（JS执行阶段）
  ├── 渲染（WXML渲染 + WXSS计算）
  ├── 绘制（图层合成）
  └── 系统开销（GC、系统调用）

关键指标：
  ├── 首屏渲染时间 < 1.5s
  ├── setData 单次数据量 < 256KB
  ├── setData 调用频率 < 20次/秒
  ├── WXML 节点数量 < 1000
  ├── 图片懒加载覆盖率 > 80%
  └── 主包体积 < 1.5MB
```

## 工作流程（Superpowers 增强版）

### Step 1: 理解需求
- 阅读PRD文档和技术方案
- 明确功能范围和技术选型
- 确认开发优先级
- 识别可测试的验收标准

### Step 2: 项目初始化
- 创建项目结构
- 配置app.json
- 安装依赖（Taro/uni-app）
- **配置测试环境（Jest + miniprogram-simulate）**

### Step 3: TDD 核心功能开发

```
对于每个功能模块，严格遵循 TDD 流程：

  3a. 页面开发
  ├── 编写页面测试用例（RED）
  ├── 运行测试确认失败
  ├── 实现页面逻辑（GREEN）
  ├── 运行测试确认通过
  └── 重构优化（REFACTOR）

  3b. 组件封装
  ├── 编写组件测试用例（RED）
  ├── 运行测试确认失败
  ├── 实现组件逻辑（GREEN）
  ├── 运行测试确认通过
  └── 重构优化（REFACTOR）

  3c. 微信能力集成
  ├── 编写工具函数测试（RED）
  ├── 实现封装函数（GREEN）
  └── 真机验证微信API行为

  3d. 状态管理实现
  ├── 编写Store测试用例（RED）
  ├── 实现Store逻辑（GREEN）
  └── 验证响应式更新
```

### Step 4: 性能优化
- 分包加载配置
- 图片优化
- 数据缓存
- 列表优化
- **性能指标验证（首屏 < 1.5s, setData < 256KB）**

### Step 5: 测试与调试
- **运行全量单元测试（npm test）**
- 微信开发者工具调试
- 真机测试（iOS + Android）
- 性能测试
- **完成前验证（verification-before-completion）**

### Step 6: 代码审查
- ESLint 检查
- 测试覆盖率检查（目标 > 80%）
- 代码规范审查
- **修复审查问题 → 重新运行测试**

## 子代理并行开发模式

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🤖 小程序子代理并行开发模式
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

主代理（协调者）
    │
    │  任务拆分原则：
    │  ├── 按层次拆分（页面/组件/工具/服务）
    │  ├── 按分包拆分（主包/package-order/package-product/...）
    │  └── 每个子任务可独立测试
    │
    ├── 子代理 A: 页面层开发
    │   ├── Task A-1: pages/index（TDD）
    │   │   ├── 编写测试用例
    │   │   ├── 实现页面逻辑
    │   │   └── 验证测试通过
    │   ├── Task A-2: pages/category（TDD）
    │   └── Task A-3: pages/cart（TDD）
    │
    ├── 子代理 B: 组件层开发
    │   ├── Task B-1: product-card 组件（TDD）
    │   │   ├── 编写测试用例
    │   │   ├── 实现组件逻辑
    │   │   └── 验证测试通过
    │   ├── Task B-2: search-bar 组件（TDD）
    │   └── Task B-3: empty-state 组件（TDD）
    │
    ├── 子代理 C: 工具/服务层开发
    │   ├── Task C-1: utils/wechat.js（TDD）
    │   ├── Task C-2: services/request.js（TDD）
    │   ├── Task C-3: stores/userStore.js（TDD）
    │   └── Task C-4: utils/optimize.js（TDD）
    │
    └── 子代理 D: 集成联调（等 A/B/C 完成）
        ├── Task D-1: 前后端联调
        ├── Task D-2: 真机测试
        ├── Task D-3: 性能测试
        └── Task D-4: 回归测试

依赖关系：
  A、B、C 可并行开发
  D 依赖 A、B、C 全部完成
  每个子任务独立 TDD 开发
  合并时运行全量测试

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

## 输出物

1. **源代码**
   - `pages/` - 页面代码
   - `components/` - 组件代码
   - `utils/` - 工具函数
   - `services/` - 服务层
   - `stores/` - 状态管理

2. **测试代码**（Superpowers 新增）
   - `tests/pages/` - 页面单元测试
   - `tests/components/` - 组件单元测试
   - `tests/utils/` - 工具函数单元测试
   - `tests/services/` - 服务层单元测试
   - `tests/stores/` - Store 单元测试

3. **配置文件**
   - `app.json` - 全局配置
   - `app.js` - 入口文件
   - `project.config.json` - 项目配置
   - `jest.config.js` - 测试配置（新增）

4. **文档**
   - `README.md` - 项目说明
   - `DEVELOPMENT.md` - 开发文档
   - `API.md` - 接口文档

## 检查清单（Superpowers 增强版）

### 代码质量检查
- [ ] 项目结构符合规范
- [ ] 代码通过 ESLint 检查
- [ ] 无 console.log 残留
- [ ] 代码审查无 Critical 问题

### 功能检查
- [ ] 核心功能已实现
- [ ] 微信能力集成正常
- [ ] 分包加载配置正确
- [ ] 性能优化完成

### Superpowers 测试检查（新增）
- [ ] 每个核心 Page 有对应测试用例
- [ ] 每个核心 Component 有对应测试用例
- [ ] 每个工具函数有对应测试用例
- [ ] 每个服务模块有对应测试用例
- [ ] 单元测试全部通过（npm test）
- [ ] 测试覆盖率 > 80%

### 平台检查
- [ ] 微信开发者工具运行正常
- [ ] 真机测试通过（iOS）
- [ ] 真机测试通过（Android）
- [ ] 微信审核规范检查通过

### 性能检查（新增）
- [ ] 主包体积 < 1.5MB
- [ ] 总包体积 < 2MB
- [ ] 首屏渲染时间 < 1.5s
- [ ] setData 单次数据量 < 256KB
- [ ] 图片懒加载覆盖率 > 80%

## 反模式警告

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
❌ 小程序开发反模式 vs 正确做法
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

❌ 写完页面再补测试
   ✅ 正确：先写测试用例，再写页面实现
   （TDD RED-GREEN-REFACTOR）

❌ 只在模拟器测试不真机测试
   ✅ 正确：模拟器 + 真机双重测试
   （iOS + Android 至少各覆盖一台）

❌ 不做分包直接超包
   ✅ 正确：提前规划分包策略
   （主包 < 1.5MB，总包 < 2MB）

❌ setData 传递大量数据
   ✅ 正确：只传递视图所需的最小数据集
   （单次 setData < 256KB）

❌ 不做错误处理直接使用API
   ✅ 正确：统一封装请求，统一错误处理
   （通过 request.js 拦截器处理）

❌ 图片不压缩直接使用
   ✅ 正确：使用CDN图片处理 + lazy-load
   （optimizeImage + mode="aspectFill" + lazy-load）

❌ 页面卸载不清除定时器/监听
   ✅ 正确：在 onUnload 中清除所有副作用
   （clearTimeout + removeEventListener）

❌ 频繁调用 setData 更新视图
   ✅ 正确：合并数据更新，使用 debounce/throttle
   （减少 setData 调用频率）

❌ 调试完成不清理 console.log
   ✅ 正确：提交前清除所有调试日志
   （ESLint no-console 规则）

❌ 不做弱网/离线处理
   ✅ 正确：本地缓存 + 网络状态监听 + 友好提示
   （wx.onNetworkStatusChange + cache）

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

## 最佳实践

1. **代码规范**
   - 使用ES6+语法
   - 遵循ESLint规则
   - 函数和组件必须有文档注释
   - 提交前运行 ESLint + Prettier

2. **性能优化**
   - 图片懒加载
   - 列表虚拟滚动
   - 数据本地缓存
   - 分包加载
   - setData 数据最小化
   - 避免频繁 setData

3. **用户体验**
   - 加载状态提示
   - 错误处理
   - 空状态处理
   - 分享配置
   - 弱网/离线友好

4. **微信规范**
   - 遵循微信设计规范
   - 符合微信审核标准
   - 用户隐私保护

5. **测试规范**（Superpowers 新增）
   - 每个核心页面编写单元测试
   - 每个可复用组件编写单元测试
   - 每个工具函数编写单元测试
   - 测试覆盖率目标 > 80%
   - 提交前运行全量测试
   - 真机测试覆盖 iOS + Android

6. **调试规范**（Superpowers 新增）
   - 遵循系统化4步调试法
   - 真机调试覆盖关键功能
   - 使用 vConsole 收集线上问题
   - 性能指标持续监控

---

**规则版本**：v2.0
**适用工作流**：6A（Assemble 节点）
**核心理念**：Superpowers 四原则（TDD、系统性、简化、证据）
**测试框架**：Jest + miniprogram-simulate
**更新日期**：2026-04-07

## 版本更新记录

| 版本 | 日期 | 更新内容 |
|------|------|----------|
| **v2.0** | **2026-04-07** | **重大升级：集成Superpowers理念，新增TDD（miniprogram-simulate）、系统化调试、子代理并行开发、完成前验证、反模式警告等机制** |
| v1.0 | 2026-04-01 | 初始版本，定义7大核心能力与代码示例 |
