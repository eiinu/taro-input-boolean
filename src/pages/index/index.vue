<template>
  <view class="index">
    <input placeholder="可正常输入"/>
    <input :disabled="false" placeholder="被禁用"/>
    <input :disabled="true" placeholder="被禁用"/>
  </view>
</template>
