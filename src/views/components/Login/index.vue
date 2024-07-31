<script setup lang="ts">
import { ref } from "vue";
import { showToast } from "vant";

const username = ref("");
const password = ref("");
const showPassword = ref(false);
const onSubmit = async (values: any) => {
  console.log("submit", values);
};
// 切换密码显示状态
const toggleShowPassword = () => {
  showPassword.value = !showPassword.value;
};
</script>

<template>
  <div class="login-page">
    <van-form @submit="onSubmit">
      <van-cell-group inset>
        <van-field
          v-model="username"
          name="username"
          label="用户名"
          placeholder="用户名"
          :rules="[{ required: true, message: '请填写用户名' }]"
        />
        <van-field
          v-model="password"
          :type="showPassword ? 'text' : 'password'"
          name="password"
          label="密码"
          placeholder="密码"
          :rules="[{ required: true, message: '请填写密码' }]"
          :right-icon="showPassword ? 'eye' : 'eye-o'"
          @click-right-icon="toggleShowPassword"
        />
      </van-cell-group>
      <div style="margin: 16px">
        <van-button round block type="primary" native-type="submit">
          提交
        </van-button>
      </div>
    </van-form>
  </div>
</template>
