---
layout: default
title: 打赏老铁
permalink: /donate/
---

# 打赏作者

## 感谢支持

感谢您访问我们的网站并使用我们提供的资源。如果您觉得我们的内容对您有所帮助，欢迎通过以下方式打赏支持我们，您的每一份支持都将激励我们继续提供更好的内容。

## 打赏方式

<div class="donate-methods">
  <div class="donate-card">
    <h3>微信打赏</h3>
    <div class="qr-code">
      <img src="/assets/images/weixin.png" alt="微信打赏二维码" style="max-width: 100%; max-height: 100%;">
    </div>
  </div>
  
  <div class="donate-card">
    <h3>支付宝打赏</h3>
    <div class="qr-code">
      <p>支付宝扫码支付</p>
      <p style="font-size: 14px; color: #666; margin-top: 10px;">（请在此处放置支付宝二维码）</p>
    </div>
  </div>
</div>

## 打赏说明

1. 打赏金额随意，多少都是您的一片心意
2. 打赏后可在下方留言，我们会尽快回复
3. 所有打赏将用于网站维护和内容更新

{% include comment_form.html %}

<style>
  .donate-methods {
    display: flex;
    gap: 40px;
    justify-content: center;
    margin: 40px 0;
    flex-wrap: wrap;
  }
  
  .donate-card {
    text-align: center;
    background-color: #ffffff;
    padding: 20px;
    border-radius: 12px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    width: 250px;
  }
  
  .donate-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 5px 15px rgba(0,0,0,0.15);
  }
  
  .qr-code {
      width: 200px;
      height: 200px;
      background-color: #ffffff;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 8px;
      margin: 15px auto;
      border: 1px solid #eaeaea;
      overflow: hidden;
      position: relative;
    }
    
    .qr-code img {
      max-width: 100% !important;
      max-height: 100% !important;
      width: auto !important;
      height: auto !important;
      object-fit: contain;
    }
  
  .donate-card h3 {
    color: #333;
    margin-bottom: 15px;
    font-size: 18px;
  }
  
  @media (max-width: 768px) {
    .donate-methods {
      flex-direction: column;
      align-items: center;
      gap: 20px;
    }
    
    .donate-card {
      width: 100%;
      max-width: 280px;
    }
  }
</style>