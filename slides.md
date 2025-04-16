---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://image-assets.eu-2.volcanic.cloud/api/v1/assets/images/211f19435904e82bc0b5d9a45af97a02?webp_fallback=png
# some information about your slides (markdown enabled)
title: QuantRL
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
hideInToc: true 
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# open graph
# seoMeta:
#  ogImage: https://cover.sli.dev
---

# QuantRL

<p class="subtitle">Algorithmic Trading Strategy Powered By Reinforcement Learning</p>

<div @click="$slidev.nav.next" class="mt-12 py-1" hover:bg="white op-10">
  Press Space for next page <carbon:arrow-right />
</div>

<style>
.subtitle {
  opacity: 0.9;
  font-weight: 500;
  font-size: 1.25rem;
}
</style>

<div class="abs-br m-6 text-xl">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="slidev-icon-btn">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

---
layout: default
hideInToc: true
transition: fade-in
---


# Table of contents

<Toc maxDepth="1"></Toc>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
transition: fade-out
---

# Motivation
<div class="text-gray-500 mb-4 text-lg">Existing RL projects applied to trading often fall short due to oversimplification and lack of robustness</div>
<div class="grid grid-cols-12 gap-0">

<div class="col-span-5 pr-4">

<h4 
  class="text-blue-600 mb-3 flex items-center text-lg"
  v-motion
  :initial="{ opacity: 0 }"
  :enter="{ opacity: 1, transition: { delay: 300, duration: 300 } }"
>
  <carbon-search class="mr-2" /> Observations:
</h4>

<div v-motion :initial="{ y: 50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 400, duration: 300 } }">
  <div class="mb-4">
    <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 500, duration: 200 } }" class="flex items-center"><span class="mr-2">📝</span> Unrealistic market dynamics</div>
    <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 600, duration: 200 } }" class="flex items-center"><span class="mr-2">🧩</span> Inadequate State Representation</div>
    <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 700, duration: 200 } }" class="flex items-center"><span class="mr-2">💸</span> Ignoring Costs & Slippage</div>
    <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 800, duration: 200 } }" class="flex items-center"><span class="mr-2">🤔</span> Poor Reward Shaping</div>
    <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 900, duration: 200 } }" class="flex items-center"><span class="mr-2">🛒</span> Limited Action Space / Order Types</div>
  </div>
</div>

<div v-motion :initial="{ y: 50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 1100, duration: 300 } }">
  <h4 
      class="text-blue-600 mb-3 flex items-center text-lg"
      v-motion
      :initial="{ opacity: 0 }"
      :enter="{ opacity: 1, transition: { delay: 1100, duration: 300 } }"
    >
      <div class="i-carbon-catalog mr-2"></div> Some examples:
    </h4>

  <div class="space-y-3 text-sm">
    <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 1200, duration: 200 } }">
      <a href="https://github.com/AminHP/gym-anytrading" target="_blank" class="inline-flex items-center px-3 py-1 rounded-full bg-gray-100 hover:bg-blue-100 transition-colors border border-gray-200 hover:border-blue-300">
        <carbon:logo-github class="mr-1 text-blue-600" /> <span class="font-medium">Gym-AnyTrading</span>
      </a>
    </div>
    <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 1300, duration: 200 } }">
      <a href="https://github.com/AI4Finance-Foundation/FinRL" target="_blank" class="inline-flex items-center px-3 py-1 rounded-full bg-gray-100 hover:bg-blue-100 transition-colors border border-gray-200 hover:border-blue-300">
        <carbon:logo-github class="mr-1 text-blue-600" /> <span class="font-medium">FinRL</span>
      </a>
    </div>
    <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 1400, duration: 200 } }">
      <a href="https://github.com/ClementPerroud/Gym-Trading-Env" target="_blank" class="inline-flex items-center px-3 py-1 rounded-full bg-gray-100 hover:bg-blue-100 transition-colors border border-gray-200 hover:border-blue-300">
        <carbon:logo-github class="mr-1 text-blue-600" /> <span class="font-medium">Gym-Trading-Env</span>
      </a>
    </div>
    <div v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 1500, duration: 200 } }">
      <a href="https://github.com/TradeMaster-NTU/TradeMaster" target="_blank" class="inline-flex items-center px-3 py-1 rounded-full bg-gray-100 hover:bg-blue-100 transition-colors border border-gray-200 hover:border-blue-300">
        <carbon:logo-github class="mr-1 text-blue-600" /> <span class="font-medium">TradeMaster-NTU</span>
      </a>
    </div>
  </div>
</div>

</div>

<div class="col-span-7 pl-4" v-motion :initial="{ x: 100, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { delay: 400, duration: 400 } }">
  <h4 
    class="text-blue-600 mb-3 flex items-center text-lg"
    v-motion
    :initial="{ opacity: 0 }"
    :enter="{ opacity: 1, transition: { delay: 500, duration: 300 } }"
  >
    <div class="i-carbon-warning-alt mr-2"></div> Skepticism:
  </h4>
  <div class="flex flex-col space-y-6">
    <div class="relative">
      <img v-motion :initial="{ scale: 0.8, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 1000, duration: 400 } }" src="./imgs/1744444356610.jpg" class="w-4/5 shadow-lg rounded-md hover:scale-105 transition-transform duration-300">
    </div>
    <div class="relative">
      <img v-motion :initial="{ scale: 0.8, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 1400, duration: 400 } }" src="./imgs/1744444286732.jpg" class="w-2/3 shadow-lg rounded-md hover:scale-105 transition-transform duration-300">
    </div>
  </div>
</div>
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
transition: fade-out
---


# Gaps in Market Realism (Examples)

<div class="col-span-8" v-motion :initial="{ x: -50, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { duration: 500 } }">

```python {4-7} {scale: 0.9}
for index in np.where(actions < -min_action)[0]:  # sell_index:
    if price[index] > 0:  # Sell only if current asset is > 0
        sell_num_shares = min(self.stocks[index], -actions[index])
        self.stocks[index] -= sell_num_shares
        self.cash += (
            price[index] * sell_num_shares * (1 - self.sell_cost_pct)
        )
        self.stocks_cool_down[index] = 0
```
<div class="text-sm text-gray-500 mt-2">
  Simplistic transaction model: Only market orders
</div>

```python
# ... calculate new total_asset based on current prices and holdings ...
reward = (total_asset - self.total_asset) * self.reward_scaling
# ... update self.total_asset for the next step ...

# ... accumulate discounted reward ...
self.gamma_reward = self.gamma_reward * self.gamma + reward

# ... at the very end of the episode ...
if done:
    reward = self.gamma_reward # Final step's reward is replaced
    self.episode_return = total_asset / self.initial_total_asset
```
<div class="text-sm text-gray-500 mt-2">
  Does not account for anything else other than the Portfolio Value
</div>


</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
transition: slide-up
---

# Scope and Deliverables
What we are trying to achieve

<div class="grid grid-cols-2 gap-8">
<div v-motion :initial="{ x: -100, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { duration: 800 } }" class="bg-white bg-opacity-90 p-6 rounded-lg shadow-md border-l-4 border-green-500">

## Hypothesis
<div class="text-gray-600 mb-6 text-lg font-light">Reinforcement Learning can significantly outperform in trading when given:</div>


<div class="space-y-4">
  <div class="flex items-start">
    <div class="text-green-500 text-xl mr-3">✓</div>
    <div>Better designed market environments</div>
  </div>
  <div class="flex items-start">
    <div class="text-green-500 text-xl mr-3">✓</div>
    <div>Realistic action spaces</div>
  </div>
  <div class="flex items-start">
    <div class="text-green-500 text-xl mr-3">✓</div>
    <div>Proper reward shaping mechanisms</div>
  </div>
</div>
</div>

<div v-motion :initial="{ x: 100, opacity: 0 }" :enter="{ x: 0, opacity: 1, transition: { duration: 800, delay: 300 } }" class="bg-white bg-opacity-90 p-6 rounded-lg shadow-md border-l-4 border-blue-500">

## Project Deliverables
<div class="space-y-4 mt-4">
  <div class="flex items-start">
    <div v-motion :initial="{ scale: 0, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 800, duration: 300 } }" class="flex-shrink-0 h-10 w-10 flex items-center justify-center rounded-full bg-blue-100 text-blue-600 mr-3">
      <div class="i-carbon-finance text-xl"></div>
    </div>
    <div class="pt-1">Enhanced trading environment with realistic market dynamics</div>
  </div>
  <div class="flex items-start">
    <div v-motion :initial="{ scale: 0, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 1000, duration: 300 } }" class="flex-shrink-0 h-10 w-10 flex items-center justify-center rounded-full bg-blue-100 text-blue-600 mr-3">
      <div class="i-carbon-chart-line-data text-xl"></div>
    </div>
    <div class="pt-1">Performance benchmarks against traditional methods</div>
  </div>
  <div class="flex items-start">
    <div v-motion :initial="{ scale: 0, opacity: 0 }" :enter="{ scale: 1, opacity: 1, transition: { delay: 1200, duration: 300 } }" class="flex-shrink-0 h-10 w-10 flex items-center justify-center rounded-full bg-blue-100 text-blue-600 mr-3">
      <div class="i-carbon-analytics text-xl"></div>
    </div>
    <div class="pt-1">Analysis of how environment design affects performance</div>
  </div>
</div>
</div>
</div>


<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
transition: slide-down
---

# Auxiliary Data to Augment the Environment
Additional data sources considered to enhance the states and observations

<div class="grid grid-cols-2 gap-x-8 gap-y-6 mt-4">
  <div v-motion :initial="{ y: 50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 300 } }">
    <div class="flex items-center mb-2">
      <div class="h-8 w-8 rounded-full bg-blue-100 flex items-center justify-center mr-2 text-lg">
        📊
      </div>
      <h3 class="text-lg font-semibold text-blue-600">Technical Indicators</h3>
    </div>
    <ul class="ml-10 space-y-1 text-sm text-gray-700">
      <li class="flex items-center">
        <div class="text-blue-500 mr-2 text-xs">▶</div>
        Moving averages (SMA, EMA, VWAP)
      </li>
      <li class="flex items-center">
        <div class="text-blue-500 mr-2 text-xs">▶</div>
        Oscillators (RSI, MACD, Stochastic)
      </li>
      <li class="flex items-center">
        <div class="text-blue-500 mr-2 text-xs">▶</div>
        Volatility indicators (Bollinger Bands, ATR)
      </li>
    </ul>
  </div>

  <div v-motion :initial="{ y: 50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 450 } }">
    <div class="flex items-center mb-2">
      <div class="h-8 w-8 rounded-full bg-green-100 flex items-center justify-center mr-2 text-lg">
        💹
      </div>
      <h3 class="text-lg font-semibold text-green-600">Fundamental Data (YFinance)</h3>
    </div>
    <ul class="ml-10 space-y-1 text-sm text-gray-700">
      <li class="flex items-center">
        <div class="text-green-500 mr-2 text-xs">▶</div>
        Financial statements (income, balance sheets)
      </li>
      <li class="flex items-center">
        <div class="text-green-500 mr-2 text-xs">▶</div>
        Key Profitability Ratio (ROA, ROE)
      </li>
    </ul>
  </div>

  <div v-motion :initial="{ y: 50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 600 } }">
    <div class="flex items-center mb-2">
      <div class="h-8 w-8 rounded-full bg-amber-100 flex items-center justify-center mr-2 text-lg">
        🌐
      </div>
      <h3 class="text-lg font-semibold text-amber-600">Macro & Sector Data (FMP)</h3>
    </div>
    <ul class="ml-10 space-y-1 text-sm text-gray-700">
      <li class="flex items-center">
        <div class="text-amber-500 mr-2 text-xs">▶</div>
        Sector performance
      </li>
      <li class="flex items-center">
        <div class="text-amber-500 mr-2 text-xs">▶</div>
        Economic indicators (GDP, CPI, Non-farm payroll)
      </li>
      <li class="flex items-center">
        <div class="text-amber-500 mr-2 text-xs">▶</div>
        Analyst ratings & price targets
      </li>
    </ul>
  </div>

  <div v-motion :initial="{ y: 50, opacity: 0 }" :enter="{ y: 0, opacity: 1, transition: { delay: 750 } }">
    <div class="flex items-center mb-2">
      <div class="h-8 w-8 rounded-full bg-purple-100 flex items-center justify-center mr-2 text-lg">
        📰
      </div>
      <h3 class="text-lg font-semibold text-purple-600">News & Events (Alpaca/FMP)</h3>
    </div>
    <ul class="ml-10 space-y-1 text-sm text-gray-700">
      <li class="flex items-center">
        <div class="text-purple-500 mr-2 text-xs">▶</div>
        Sentiment analysis from stock news
      </li>
      <li class="flex items-center">
        <div class="text-purple-500 mr-2 text-xs">▶</div>
        Calendar events (e.g., Fed announcement)
      </li>
    </ul>
  </div>
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
transition: fade-in
---
# Designing the Custom Trading Environment
Action Spaces, States, Reward

<div grid="~ cols-3 gap-6" class="mt-10">

<div class="border rounded-2xl p-6 shadow-md hover:shadow-lg transition bg-gray-50">
  <div class="text-4xl mb-3">🎯</div>
  <div class="text-xl font-bold text-gray-800 mb-2">Action</div>
  <div class="text-sm text-gray-600 leading-relaxed">
    The decision made by the agent at each step, influencing the environment.
  </div>
</div>

<div class="border rounded-2xl p-6 shadow-md hover:shadow-lg transition bg-gray-50">
  <div class="text-4xl mb-3">🌍</div>
  <div class="text-xl font-bold text-gray-800 mb-2">State</div>
  <div class="text-sm text-gray-600 leading-relaxed">
    A snapshot of the environment that the agent uses to determine its next move.
  </div>
</div>

<div class="border rounded-2xl p-6 shadow-md hover:shadow-lg transition bg-gray-50">
  <div class="text-4xl mb-3">💰</div>
  <div class="text-xl font-bold text-gray-800 mb-2">Reward</div>
  <div class="text-sm text-gray-600 leading-relaxed">
    Feedback signal that tells the agent how well it's performing toward its goal.
  </div>
</div>

</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
transition: fade-in
hideInToc: true 
---

# Designing the Custom Trading Environment (cont.)
Action Spaces, States, Reward

## Sub-section: Environment Complexity

- Realistic transaction costs  
- Slippage modeling  
- Market impact consideration  
- Limit/stop vs. market orders  
- Liquidity constraints  

## Sub-section: Signal Delay and Event Handling

- Time-varying volatility regimes  
- Delayed reward signals  
- Spread simulation  
- Price impact from large orders  
- Event-driven reactions

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
transition: fade-in
layout: center
class: text-center
---

# Results and Findings
Experiment Setup

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
layout: center
class: text-center
---

# Thank You

<div class="mt-8">
  <a 
    href="https://github.com/whanyu1212/QuantRL" 
    target="_blank" 
    class="inline-flex items-center px-6 py-3 rounded-lg bg-blue-600 text-white font-semibold shadow-md hover:bg-blue-700 transition-colors duration-300"
  >
    <carbon:logo-github class="mr-2" />
    View Project Repository
  </a>
</div>

<div class="mt-6 text-gray-500 text-sm">
  Questions? Feel free to reach out!
</div>
