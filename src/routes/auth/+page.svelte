<script>
  // Reactive variable to track the form mode
  let isSignIn = true;

  // Function to toggle between Sign In and Sign Up modes
  function toggleMode() {
    isSignIn = !isSignIn;
  }
</script>

<div class="h-screen bg-gray-900">
  <div class="h-full">
    <div class="flex min-h-full flex-col justify-center px-6 py-12 lg:px-8">
      <!-- Logo and Heading -->
      <div class="sm:mx-auto sm:w-full sm:max-w-sm">
        <img
          class="mx-auto h-10 w-auto"
          src="https://tailwindui.com/plus/img/logos/mark.svg?color=indigo&shade=500"
          alt="Your Company"
        />
        <h2 class="mt-10 text-center text-2xl font-bold leading-9 tracking-tight text-white">
          {#if isSignIn}
            Sign in to Kold Leads
          {:else}
            Sign up to Kold Leads
          {/if}
        </h2>
      </div>

      <!-- Form -->
      <div class="mt-10 sm:mx-auto sm:w-full sm:max-w-sm">
        <form
          class="space-y-6"
          action={isSignIn ? "?/login" : "?/signup"}
          method="POST"
        >
          <!-- Email Field -->
          <div>
            <label
              for="email"
              class="block text-sm font-medium leading-6 text-white"
              >Email address</label
            >
            <div class="mt-2">
              <input
                id="email"
                name="email"
                type="email"
                autocomplete="email"
                required
                class="block w-full rounded-md border-0 bg-white/5 py-1.5 text-white shadow-sm ring-1 ring-inset ring-white/10 focus:ring-2 focus:ring-inset focus:ring-indigo-500 sm:text-sm sm:leading-6"
              />
            </div>
          </div>

          <!-- Password Field -->
          <div>
            <div class="flex items-center justify-between">
              <label
                for="password"
                class="block text-sm font-medium leading-6 text-white"
                >Password</label
              >
              {#if isSignIn}
                <div class="text-sm">
                  <a
                    href="#"
                    class="font-semibold text-indigo-400 hover:text-indigo-300"
                    >Forgot password?</a
                  >
                </div>
              {/if}
            </div>
            <div class="mt-2">
              <input
                id="password"
                name="password"
                type="password"
                autocomplete="current-password"
                required
                class="block w-full rounded-md border-0 bg-white/5 py-1.5 text-white shadow-sm ring-1 ring-inset ring-white/10 focus:ring-2 focus:ring-inset focus:ring-indigo-500 sm:text-sm sm:leading-6"
              />
            </div>
          </div>

          <!-- Submit Button -->
          <div class="flex space-x-4">
            <button
              type="submit"
              class="flex-1 justify-center rounded-md bg-indigo-500 px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-indigo-400 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-500"
            >
              {#if isSignIn}
                Sign in
              {:else}
                Sign up
              {/if}
            </button>
          </div>
        </form>

        <!-- Toggle Link -->
        <p class="mt-10 text-center text-sm text-gray-400">
          {#if isSignIn}
            Not a member?
            <a
              href="#"
              on:click|preventDefault={toggleMode}
              class="font-semibold leading-6 text-indigo-400 hover:text-indigo-300"
              >Start a 14 day free trial</a
            >
          {:else}
            Already have an account?
            <a
              href="#"
              on:click|preventDefault={toggleMode}
              class="font-semibold leading-6 text-indigo-400 hover:text-indigo-300"
              >Sign in</a
            >
          {/if}
        </p>
      </div>
    </div>
  </div>
</div>
