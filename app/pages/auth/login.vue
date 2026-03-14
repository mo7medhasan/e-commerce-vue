<template>
  <div class="min-h-screen flex items-center justify-center px-4 py-12">
     <div class="max-w-md bg-linear-to-br from-slate-100 via-indigo-50 to-violet-100 rounded-2xl shadow-2xl shadow-indigo-500/10 border border-white/40 p-8 sm:p-10 transition-all duration-500">
            <div class="text-center mb-8">
                <h1 class="text-3xl font-bold text-slate-800 mb-2">Welcome Back</h1>
                <p class="text-slate-600">Please enter your details to sign in</p>
            </div>
            <form @submit.prevent="handleLogin" class="space-y-6">
                <div class="space-y-2">
                    <label for="email" class="block text-sm font-medium text-slate-700">Email Address</label>
                    <input type="email" id="email" v-model="form.email" required class="w-full px-4 py-3 rounded-lg border border-slate-300 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:border-transparent transition-all duration-200" placeholder="Enter your email">
                </div>
                <div class="space-y-2">
                    <label for="password" class="block text-sm font-medium text-slate-700">Password</label>
                    <input type="password" id="password" v-model="form.password" required class="w-full px-4 py-3 rounded-lg border border-slate-300 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:border-transparent transition-all duration-200" placeholder="Enter your password">
                </div>
                <div class="flex items-center justify-between">
                    <div class="flex items-center">
                        <input type="checkbox" id="rememberMe" v-model="form.rememberMe" class="h-4 w-4 text-indigo-600 border-slate-300 rounded focus:ring-indigo-500">
                        <label for="rememberMe" class="ml-2 block text-sm text-slate-600">Remember me</label>
                    </div>
                    <a href="#" class="text-sm font-medium text-indigo-600 hover:text-indigo-500 transition-colors duration-200">Forgot your password?</a>
                </div>
                <button type="submit" :disabled="isLoading" class="w-full bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-3 px-4 rounded-lg transition-all duration-200 disabled:opacity-50 disabled:cursor-not-allowed">
                    {{ isLoading ? 'Signing in...' : 'Sign In' }}
                </button>
            </form>
     </div>

  </div>
</template>

<script setup>
definePageMeta({
  layout: "auth",
});

const form = reactive({
  email: "",
  password: "",
  rememberMe: false,
});

const showPassword = ref(false);
const isLoading = ref(false);

const handleLogin = async () => {
  isLoading.value = true;
  try {
    // TODO: Implement actual login logic
    console.log("Login attempt:", {
      email: form.email,
      password: form.password,
      rememberMe: form.rememberMe,
    });

    // Simulate API call
    await new Promise((resolve) => setTimeout(resolve, 1500));

    // Navigate to home or dashboard after successful login
    // await navigateTo('/');
  } catch (error) {
    console.error("Login failed:", error);
  } finally {
    isLoading.value = false;
  }
};
</script>
