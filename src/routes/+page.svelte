<script>
    // Reactive variable to manage the mobile menu state
    let isMenuOpen = false;
  
    // Function to toggle the mobile menu
    function toggleMenu() {
      isMenuOpen = !isMenuOpen;
    }

    // Reactive variable to manage payment frequency
    let frequency = 'monthly'; // default to monthly

    // Pricing data
    const pricingPlans = {
      freelancer: {
        monthly: 15,
        annually: 150, // Example: 2 months free
        features: [
          "5 products",
          "Up to 1,000 subscribers",
          "Basic analytics",
          "48-hour support response time"
        ]
      },
      startup: {
        monthly: 30,
        annually: 300, // Example: 2 months free
        features: [
          "25 products",
          "Up to 10,000 subscribers",
          "Advanced analytics",
          "24-hour support response time",
          "Marketing automations"
        ]
      },
      enterprise: {
        monthly: 48,
        annually: 480, // Example: 2 months free
        features: [
          "Unlimited products",
          "Unlimited subscribers",
          "Advanced analytics",
          "1-hour, dedicated support response time",
          "Marketing automations",
          "Custom reporting tools"
        ]
      }
    };

    // Function to get price based on frequency
    function getPrice(plan) {
      return frequency === 'monthly' ? `$${pricingPlans[plan].monthly}` : `$${pricingPlans[plan].annually}`;
    }

    // Function to get payment frequency label
    function getFrequencyLabel() {
      return frequency === 'monthly' ? '/month' : '/year';
    }
</script>
  <div class="bg-gray-900 text-white">
    <!-- Header with Navbar -->
    <header class="absolute inset-x-0 top-0 z-50">
      <nav class="flex items-center justify-between p-6 lg:px-8" aria-label="Global">
        <div class="flex lg:flex-1">
          <a href="#" class="-m-1.5 p-1.5">
            <span class="sr-only">Koldleads</span>
            <img class="h-8 w-auto" src="https://tailwindui.com/plus/img/logos/mark.svg?color=indigo&shade=600" alt="Koldleads">
          </a>
        </div>
        <div class="flex lg:hidden">
          <button type="button" on:click={toggleMenu} class="-m-2.5 inline-flex items-center justify-center rounded-md p-2.5 text-gray-300 hover:text-white focus:outline-none">
            <span class="sr-only">Open main menu</span>
            <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true">
              <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5" />
            </svg>
          </button>
        </div>
        <div class="hidden lg:flex lg:gap-x-12">
          <a href="#features" class="text-sm font-semibold leading-6 text-gray-300 hover:text-white">Features</a>
          <a href="#pricing" class="text-sm font-semibold leading-6 text-gray-300 hover:text-white">Pricing</a>
          <a href="#company" class="text-sm font-semibold leading-6 text-gray-300 hover:text-white">Company</a>
        </div>
        <div class="hidden lg:flex lg:flex-1 lg:justify-end">
          <a href="#cta" class="text-sm font-semibold leading-6 text-gray-300 hover:text-white">Start Trial <span aria-hidden="true">→</span></a>
        </div>
      </nav>
  
      <!-- Mobile Menu -->
      {#if isMenuOpen}
        <div class="lg:hidden" role="dialog" aria-modal="true">
          <!-- Overlay -->
          <div class="fixed inset-0 bg-black bg-opacity-25" on:click={toggleMenu}></div>
          <!-- Mobile Menu Panel -->
          <div class="fixed inset-y-0 right-0 z-50 w-full max-w-sm overflow-y-auto bg-gray-800 p-6 shadow-xl">
            <div class="flex items-center justify-between">
              <a href="#" class="-m-1.5 p-1.5">
                <span class="sr-only">Koldleads</span>
                <img class="h-8 w-auto" src="https://tailwindui.com/plus/img/logos/mark.svg?color=indigo&shade=600" alt="Koldleads">
              </a>
              <button type="button" on:click={toggleMenu} class="-m-2.5 rounded-md p-2.5 text-gray-300 hover:text-white focus:outline-none">
                <span class="sr-only">Close menu</span>
                <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                </svg>
              </button>
            </div>
            <div class="mt-6 flow-root">
              <div class="-my-6 divide-y divide-gray-700">
                <div class="space-y-2 py-6">
                  <a href="#features" class="-mx-3 block rounded-lg px-3 py-2 text-base font-semibold leading-7 text-gray-300 hover:bg-gray-700">Features</a>
                  <a href="#pricing" class="-mx-3 block rounded-lg px-3 py-2 text-base font-semibold leading-7 text-gray-300 hover:bg-gray-700">Pricing</a>
                  <a href="#company" class="-mx-3 block rounded-lg px-3 py-2 text-base font-semibold leading-7 text-gray-300 hover:bg-gray-700">Company</a>
                </div>
                <div class="py-6">
                  <a href="#cta" class="-mx-3 block rounded-lg px-3 py-2.5 text-base font-semibold leading-7 text-gray-300 hover:bg-gray-700">Start Trial</a>
                </div>
              </div>
            </div>
          </div>
        </div>
      {/if}
    </header>
  
    <main class="isolate">
      <!-- Hero Section -->
      <div class="relative isolate overflow-hidden">
        <!-- Background SVG Patterns -->
        <svg class="absolute inset-0 -z-10 h-full w-full stroke-white/10 [mask-image:radial-gradient(100%_100%_at_top_right,white,transparent)]" aria-hidden="true">
          <defs>
            <pattern id="hero-pattern" width="200" height="200" x="50%" y="-1" patternUnits="userSpaceOnUse">
              <path d="M.5 200V.5H200" fill="none" />
            </pattern>
          </defs>
          <svg x="50%" y="-1" class="overflow-visible fill-gray-800/20">
            <path d="M-200 0h201v201h-201Z M600 0h201v201h-201Z M-400 600h201v201h-201Z M200 800h201v201h-201Z" stroke-width="0" />
          </svg>
          <rect width="100%" height="100%" stroke-width="0" fill="url(#hero-pattern)" />
        </svg>
        <div class="absolute left-[calc(50%-4rem)] top-10 -z-10 transform-gpu blur-3xl sm:left-[calc(50%-18rem)] lg:left-48 lg:top-[calc(50%-30rem)] xl:left-[calc(50%-24rem)]" aria-hidden="true">
          <div
            class="aspect-[1108/632] w-[69.25rem] bg-gradient-to-r from-[#80caff] to-[#4f46e5] opacity-20"
            style="clip-path: polygon(73.6% 51.7%, 91.7% 11.8%, 100% 46.4%, 97.4% 82.2%, 92.5% 84.9%, 75.7% 64%, 55.3% 47.5%, 46.5% 49.4%, 45% 62.9%, 50.3% 87.2%, 21.3% 64.1%, 0.1% 100%, 5.4% 51.1%, 21.4% 63.9%, 58.9% 0.2%, 73.6% 51.7%)"
          ></div>
        </div>
        <div class="mx-auto max-w-7xl px-6 pb-24 pt-10 sm:pb-40 lg:flex lg:px-8 lg:pt-40">
          <div class="mx-auto max-w-2xl flex-shrink-0 lg:mx-0 lg:max-w-xl lg:pt-8">
            <img class="h-11" src="https://tailwindui.com/plus/img/logos/mark.svg?color=indigo&shade=500" alt="Koldleads">
            <div class="mt-24 sm:mt-32 lg:mt-16">
              <a href="#cta" class="inline-flex space-x-6">
                <span class="rounded-full bg-indigo-500/10 px-3 py-1 text-sm font-semibold leading-6 text-indigo-400 ring-1 ring-inset ring-indigo-500/20">Latest Update</span>
                <span class="inline-flex items-center space-x-2 text-sm font-medium leading-6 text-gray-300">
                  <span>Introducing Koldleads</span>
                  <svg class="h-5 w-5 text-gray-500" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
                    <path fill-rule="evenodd" d="M7.21 14.77a.75.75 0 01.02-1.06L11.168 10 7.23 6.29a.75.75 0 111.04-1.08l4.5 4.25a.75.75 0 010 1.08l-4.5 4.25a.75.75 0 01-1.06-.02z" clip-rule="evenodd" />
                  </svg>
                </span>
              </a>
            </div>
            <h1 class="mt-10 text-4xl font-bold tracking-tight text-white sm:text-6xl">
              Grow Your Agency With 300+ Million B2B Contacts (Affordably)
            </h1>
            <p class="mt-6 text-lg leading-8 text-gray-300">
              Connect with the right clients effortlessly. Our accurate lead databases help you find and engage with businesses that need your services.
            </p>
            <div class="mt-10 flex items-center gap-x-6">
              <a href="#cta" class="rounded-md bg-indigo-500 px-3.5 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-indigo-400 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-400">Start Trial</a>
              <a href="#features" class="text-sm font-semibold leading-6 text-white">Learn More <span aria-hidden="true">→</span></a>
            </div>
          </div>
          <div class="mx-auto mt-16 flex max-w-2xl sm:mt-24 lg:ml-10 lg:mr-0 lg:mt-0 lg:max-w-none lg:flex-none xl:ml-32">
            <div class="max-w-3xl flex-none sm:max-w-5xl lg:max-w-none">
              <img
                src="https://tailwindui.com/plus/img/component-images/dark-project-app-screenshot.png"
                alt="Koldleads Dashboard"
                width="2432"
                height="1442"
                class="w-[76rem] rounded-md bg-white/5 shadow-2xl ring-1 ring-white/10"
              />
            </div>
          </div>
        </div>
      </div>
  
      <!-- Logo Cloud -->
      <div class="mx-auto mt-8 max-w-7xl px-6 sm:mt-16 lg:px-8">
        <h2 class="text-center text-lg font-semibold leading-8 text-white">
          Trusted by Agencies Worldwide
        </h2>
        <div class="mx-auto mt-10 grid max-w-lg grid-cols-4 items-center gap-x-8 gap-y-10 sm:max-w-xl sm:grid-cols-6 sm:gap-x-10 lg:mx-0 lg:max-w-none lg:grid-cols-5">
          <img class="col-span-2 max-h-12 w-full object-contain lg:col-span-1" src="https://tailwindui.com/plus/img/logos/158x48/transistor-logo-white.svg" alt="Transistor" width="158" height="48">
          <img class="col-span-2 max-h-12 w-full object-contain lg:col-span-1" src="https://tailwindui.com/plus/img/logos/158x48/reform-logo-white.svg" alt="Reform" width="158" height="48">
          <img class="col-span-2 max-h-12 w-full object-contain lg:col-span-1" src="https://tailwindui.com/plus/img/logos/158x48/tuple-logo-white.svg" alt="Tuple" width="158" height="48">
          <img class="col-span-2 max-h-12 w-full object-contain sm:col-start-2 lg:col-span-1" src="https://tailwindui.com/plus/img/logos/158x48/savvycal-logo-white.svg" alt="SavvyCal" width="158" height="48">
          <img class="col-span-2 col-start-2 max-h-12 w-full object-contain sm:col-start-auto lg:col-span-1" src="https://tailwindui.com/plus/img/logos/158x48/statamic-logo-white.svg" alt="Statamic" width="158" height="48">
        </div>
      </div>
  
      <!-- Features Section -->
      <div class="mx-auto mt-32 max-w-7xl px-6 sm:mt-56 lg:px-8">
        <div class="mx-auto max-w-2xl text-center">
          <h2 class="text-base font-semibold leading-7 text-indigo-400">
            Accelerate Your Growth
          </h2>
          <p class="mt-2 text-3xl font-bold tracking-tight text-white sm:text-4xl">
            Everything You Need to Land More Clients
          </p>
          <p class="mt-6 text-lg leading-8 text-gray-300">
            Koldleads provides accurate and comprehensive lead data to help your agency connect with the right businesses, faster.
          </p>
        </div>
        <div class="mx-auto mt-16 max-w-2xl sm:mt-20 lg:mt-24 lg:max-w-none">
          <dl class="grid max-w-xl grid-cols-1 gap-x-8 gap-y-16 lg:max-w-none lg:grid-cols-3">
            <div class="flex flex-col">
              <dt class="text-base font-semibold leading-7 text-white">
                <div class="mb-6 flex h-10 w-10 items-center justify-center rounded-lg bg-indigo-500">
                  <svg
                    class="h-6 w-6 text-white"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke-width="1.5"
                    stroke="currentColor"
                    aria-hidden="true"
                  >
                    <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 13.5l10.5-11.25L12 10.5h8.25L9.75 21.75 12 13.5H3.75z" />
                  </svg>
                </div>
                Accurate Data
              </dt>
              <dd class="mt-1 flex flex-auto flex-col text-base leading-7 text-gray-300">
                <p class="flex-auto">
                  Access up-to-date and precise lead information to ensure you connect with potential clients who are actively seeking your services.
                </p>
                <p class="mt-6">
                  <a href="#cta" class="text-sm font-semibold leading-6 text-indigo-400">Start Trial <span aria-hidden="true">→</span></a>
                </p>
              </dd>
            </div>
            <div class="flex flex-col">
              <dt class="text-base font-semibold leading-7 text-white">
                <div class="mb-6 flex h-10 w-10 items-center justify-center rounded-lg bg-indigo-500">
                  <svg
                    class="h-6 w-6 text-white"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke-width="1.5"
                    stroke="currentColor"
                    aria-hidden="true"
                  >
                    <path stroke-linecap="round" stroke-linejoin="round" d="M15 19.128a9.38 9.38 0 002.625.372 9.337 9.337 0 004.121-.952 4.125 4.125 0 00-7.533-2.493M15 19.128v-.003c0-1.113-.285-2.16-.786-3.07M15 19.128v.106A12.318 12.318 0 018.624 21c-2.331 0-4.512-.645-6.374-1.766l-.001-.109a6.375 6.375 0 0111.964-3.07M12 6.375a3.375 3.375 0 11-6.75 0 3.375 3.375 0 016.75 0zm8.25 2.25a2.625 2.625 0 11-5.25 0 2.625 2.625 0 015.25 0z" />
                  </svg>
                </div>
                Easy Filtering
              </dt>
              <dd class="mt-1 flex flex-auto flex-col text-base leading-7 text-gray-300">
                <p class="flex-auto">
                  Quickly narrow down leads based on specific criteria such as industry, company size, and location to find the perfect match for your agency.
                </p>
                <p class="mt-6">
                  <a href="#cta" class="text-sm font-semibold leading-6 text-indigo-400">Start Trial <span aria-hidden="true">→</span></a>
                </p>
              </dd>
            </div>
            <div class="flex flex-col">
              <dt class="text-base font-semibold leading-7 text-white">
                <div class="mb-6 flex h-10 w-10 items-center justify-center rounded-lg bg-indigo-500">
                  <svg
                    class="h-6 w-6 text-white"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke-width="1.5"
                    stroke="currentColor"
                    aria-hidden="true"
                  >
                    <path stroke-linecap="round" stroke-linejoin="round" d="M6.75 3v2.25M17.25 3v2.25M3 18.75V7.5a2.25 2.25 0 012.25-2.25h13.5A2.25 2.25 0 0121 7.5v11.25m-18 0A2.25 2.25 0 005.25 21h13.5A2.25 2.25 0 0021 18.75m-18 0v-7.5A2.25 2.25 0 015.25 9h13.5A2.25 2.25 0 0121 11.25v7.5m-9-6h.008v.008H12v-.008zM12 15h.008v.008H12V15zm0 2.25h.008v.008H12v-.008zM9.75 15h.008v.008H9.75V15zm0 2.25h.008v.008H9.75v-.008zM7.5 15h.008v.008H7.5V15zm0 2.25h.008v.008H7.5v-.008zm6.75-4.5h.008v.008H16.5v-.008zm0 2.25h.008v.008H16.5V15zm0 2.25h.008v.008H16.5V15zm2.25-4.5h.008v.008H16.5v-.008zM16.5 15h.008v.008H16.5V15z" />
                  </svg>
                </div>
                Seamless Integration
              </dt>
              <dd class="mt-1 flex flex-auto flex-col text-base leading-7 text-gray-300">
                <p class="flex-auto">
                  Integrate Koldleads effortlessly with your existing CRM and marketing tools to streamline your workflow and maximize efficiency.
                </p>
                <p class="mt-6">
                  <a href="#cta" class="text-sm font-semibold leading-6 text-indigo-400">Start Trial <span aria-hidden="true">→</span></a>
                </p>
              </dd>
            </div>
          </dl>
        </div>
      </div>
  
      <!-- Additional Feature Section (Optional) -->
      <div class="mt-32 sm:mt-56">
        <div class="mx-auto max-w-7xl px-6 lg:px-8">
          <div class="mx-auto max-w-2xl sm:text-center">
            <h2 class="text-base font-semibold leading-7 text-indigo-400">
              Comprehensive Tools
            </h2>
            <p class="mt-2 text-3xl font-bold tracking-tight text-white sm:text-4xl">
              No Limits on Your Growth
            </p>
            <p class="mt-6 text-lg leading-8 text-gray-300">
              Whether you're a small agency or a large firm, Koldleads scales with your needs, providing the tools you need to succeed.
            </p>
          </div>
        </div>
        <div class="relative overflow-hidden pt-16">
          <div class="mx-auto max-w-7xl px-6 lg:px-8">
            <img
              src="https://tailwindui.com/plus/img/component-images/dark-project-app-screenshot.png"
              alt="Koldleads Features"
              class="mb-[-12%] rounded-xl shadow-2xl ring-1 ring-white/10"
              width="2432"
              height="1442"
            />
            <div class="relative" aria-hidden="true">
              <div class="absolute -inset-x-20 bottom-0 bg-gradient-to-t from-gray-900 pt-[7%]"></div>
            </div>
          </div>
        </div>
        <div class="mx-auto mt-16 max-w-7xl px-6 sm:mt-20 md:mt-24 lg:px-8">
          <dl class="mx-auto grid max-w-2xl grid-cols-1 gap-x-6 gap-y-10 text-base leading-7 text-gray-300 sm:grid-cols-2 lg:mx-0 lg:max-w-none lg:grid-cols-3 lg:gap-x-8 lg:gap-y-16">
            <div class="relative pl-9">
              <dt class="inline font-semibold text-white">
                <svg
                  class="absolute left-1 top-1 h-5 w-5 text-indigo-500"
                  viewBox="0 0 20 20"
                  fill="currentColor"
                  aria-hidden="true"
                >
                  <path
                    fill-rule="evenodd"
                    d="M5.5 17a4.5 4.5 0 01-1.44-8.765 4.5 4.5 0 018.302-3.046 3.5 3.5 0 014.504 4.272A4 4 0 0115 17H5.5zm3.75-2.75a.75.75 0 001.5 0V9.66l1.95 2.1a.75.75 0 101.1-1.02l-3.25-3.5a.75.75 0 00-1.1 0l-3.25 3.5a.75.75 0 101.1 1.02l1.95-2.1v4.59z"
                    clip-rule="evenodd"
                  />
                </svg>
                Push to Deploy
              </dt>
              <dd class="inline">
                Deploy your campaigns directly from Koldleads to your preferred platforms with ease.
              </dd>
            </div>
            <div class="relative pl-9">
              <dt class="inline font-semibold text-white">
                <svg
                  class="absolute left-1 top-1 h-5 w-5 text-indigo-500"
                  viewBox="0 0 20 20"
                  fill="currentColor"
                  aria-hidden="true"
                >
                  <path
                    fill-rule="evenodd"
                    d="M10 1a4.5 4.5 0 00-4.5 4.5V9H5a2 2 0 00-2 2v6a2 2 0 002 2h10a2 2 0 002-2v-6a2 2 0 00-2-2h-.5V5.5A4.5 4.5 0 0010 1zm3 8V5.5a3 3 0 10-6 0V9h6z"
                    clip-rule="evenodd"
                  />
                </svg>
                SSL Secure
              </dt>
              <dd class="inline">
                Your data is protected with top-notch SSL encryption, ensuring your leads are safe and secure.
              </dd>
            </div>
            <div class="relative pl-9">
              <dt class="inline font-semibold text-white">
                <svg
                  class="absolute left-1 top-1 h-5 w-5 text-indigo-500"
                  viewBox="0 0 20 20"
                  fill="currentColor"
                  aria-hidden="true"
                >
                  <path
                    fill-rule="evenodd"
                    d="M15.312 11.424a5.5 5.5 0 01-9.201 2.466l-.312-.311h2.433a.75.75 0 000-1.5H3.989a.75.75 0 00-.75.75v4.242a.75.75 0 001.5 0v-2.43l.31.31a7 7 0 0011.712-3.138.75.75 0 00-1.449-.39zm1.23-3.723a.75.75 0 00.219-.53V2.929a.75.75 0 00-1.5 0V5.36l-.31-.31A7 7 0 003.239 8.188a.75.75 0 101.448.389A5.5 5.5 0 0113.89 6.11l.311.31h-2.432a.75.75 0 000 1.5h4.243a.75.75 0 00.53-.219z"
                    clip-rule="evenodd"
                  />
                </svg>
              </dt>
              <dd class="inline">
                Manage your lead queues effortlessly and ensure timely follow-ups to convert leads into clients.
              </dd>
            </div>
          </dl>
        </div>
      </div>
  
      <!-- Stats Section -->
      <div class="mx-auto mt-32 max-w-7xl px-6 sm:mt-56 lg:px-8">
        <div class="mx-auto max-w-2xl lg:mx-0 lg:max-w-xl">
          <h2 class="text-base font-semibold leading-8 text-indigo-400">
            Our Success Metrics
          </h2>
          <p class="mt-2 text-3xl font-bold tracking-tight text-white sm:text-4xl">
            Trusted by Thousands of Agencies Worldwide
          </p>
          <p class="mt-6 text-lg leading-8 text-gray-300">
            Join a growing community of agencies that rely on Koldleads to connect with quality clients and drive their business forward.
          </p>
        </div>
        <dl class="mx-auto mt-16 grid max-w-2xl grid-cols-1 gap-x-8 gap-y-10 text-white sm:mt-20 sm:grid-cols-2 sm:gap-y-16 lg:mx-0 lg:max-w-none lg:grid-cols-4">
          <div class="flex flex-col gap-y-3 border-l border-white/10 pl-6">
            <dt class="text-sm leading-6">Agencies on the Platform</dt>
            <dd class="order-first text-3xl font-semibold tracking-tight">5,000+</dd>
          </div>
          <div class="flex flex-col gap-y-3 border-l border-white/10 pl-6">
            <dt class="text-sm leading-6">Leads Accessed Daily</dt>
            <dd class="order-first text-3xl font-semibold tracking-tight">750k+</dd>
          </div>
          <div class="flex flex-col gap-y-3 border-l border-white/10 pl-6">
            <dt class="text-sm leading-6">Uptime Guarantee</dt>
            <dd class="order-first text-3xl font-semibold tracking-tight">99.9%</dd>
          </div>
          <div class="flex flex-col gap-y-3 border-l border-white/10 pl-6">
            <dt class="text-sm leading-6">Campaigns Launched</dt>
            <dd class="order-first text-3xl font-semibold tracking-tight">20,000</dd>
          </div>
        </dl>
      </div>
  
      <div id="pricing" class="bg-gray-900 py-24 sm:py-32">
        <div class="mx-auto max-w-7xl px-6 lg:px-8">
          <div class="mx-auto max-w-4xl text-center">
            <h2 class="text-base font-semibold leading-7 text-indigo-400">Affordable asf</h2>
            <p class="mt-2 text-4xl font-bold tracking-tight text-white sm:text-5xl">
                Pricing
            </p>
          </div>
          <p class="mx-auto mt-6 max-w-2xl text-center text-lg leading-8 text-gray-300">
            You can upgrade / downgrade any time.
          </p>
          <div class="mt-16 flex justify-center">
            <fieldset aria-label="Payment frequency">
              <div class="grid grid-cols-2 gap-x-1 rounded-full bg-white/5 p-1 text-center text-xs font-semibold leading-5 text-white">
                <!-- Monthly Toggle -->
                <label
                  class="cursor-pointer rounded-full px-2.5 py-1"
                  class:bg-indigo-500={frequency === 'monthly'}
                  on:click={() => frequency = 'monthly'}
                >
                  <input type="radio" name="frequency" value="monthly" class="sr-only" bind:group={frequency} />
                  <span>Monthly</span>
                </label>
                <!-- Annually Toggle -->
                <label
                  class="cursor-pointer rounded-full px-2.5 py-1"
                  class:bg-indigo-500={frequency === 'annually'}
                  on:click={() => frequency = 'annually'}
                >
                  <input type="radio" name="frequency" value="annually" class="sr-only" bind:group={frequency} />
                  <span>Annually</span>
                </label>
              </div>
            </fieldset>
          </div>
          <div class="isolate mx-auto mt-10 grid max-w-md grid-cols-1 gap-8 lg:mx-0 lg:max-w-none lg:grid-cols-3">
            <!-- Starter Plan -->
            <div class="rounded-3xl p-8 ring-1 ring-white/10 xl:p-10">
              <div class="flex items-center justify-between gap-x-4">
                <h3 id="tier-starter" class="text-lg font-semibold leading-8 text-white">Starter</h3>
              </div>
              <p class="mt-4 text-sm leading-6 text-gray-300">Essential tools to find and engage with clients.</p>
              <p class="mt-6 flex items-baseline gap-x-1">
                <!-- Dynamic Price -->
                <span class="text-4xl font-bold tracking-tight text-white">{getPrice('freelancer')}</span>
                <!-- Dynamic Frequency Label -->
                <span class="text-sm font-semibold leading-6 text-gray-300">{getFrequencyLabel()}</span>
              </p>
              <a href="#" aria-describedby="tier-starter" class="mt-6 block rounded-md bg-white/10 px-3 py-2 text-center text-sm font-semibold leading-6 text-white hover:bg-white/20 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-white">Buy Plan</a>
              <ul role="list" class="mt-8 space-y-3 text-sm leading-6 text-gray-300 xl:mt-10">
                {#each pricingPlans.freelancer.features as feature}
                  <li class="flex gap-x-3">
                    <svg class="h-6 w-5 flex-none text-white" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
                      <path fill-rule="evenodd" d="M16.704 4.153a.75.75 0 01.143 1.052l-8 10.5a.75.75 0 01-1.127.075l-4.5-4.5a.75.75 0 011.06-1.06l3.894 3.893 7.48-9.817a.75.75 0 011.05-.143z" clip-rule="evenodd" />
                    </svg>
                    {feature}
                  </li>
                {/each}
              </ul>
            </div>
            <!-- Growth Plan -->
            <div class="rounded-3xl bg-white/5 p-8 ring-2 ring-indigo-500 xl:p-10">
              <div class="flex items-center justify-between gap-x-4">
                <h3 id="tier-growth" class="text-lg font-semibold leading-8 text-white">Growth</h3>
                <p class="rounded-full bg-indigo-500 px-2.5 py-1 text-xs font-semibold leading-5 text-white">Most Popular</p>
              </div>
              <p class="mt-4 text-sm leading-6 text-gray-300">Advanced tools to scale your client acquisition.</p>
              <p class="mt-6 flex items-baseline gap-x-1">
                <!-- Dynamic Price -->
                <span class="text-4xl font-bold tracking-tight text-white">{getPrice('startup')}</span>
                <!-- Dynamic Frequency Label -->
                <span class="text-sm font-semibold leading-6 text-gray-300">{getFrequencyLabel()}</span>
              </p>
              <a href="#" aria-describedby="tier-growth" class="mt-6 block rounded-md bg-indigo-500 px-3 py-2 text-center text-sm font-semibold leading-6 text-white shadow-sm hover:bg-indigo-400 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-500">Buy Plan</a>
              <ul role="list" class="mt-8 space-y-3 text-sm leading-6 text-gray-300 xl:mt-10">
                {#each pricingPlans.startup.features as feature}
                  <li class="flex gap-x-3">
                    <svg class="h-6 w-5 flex-none text-white" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
                      <path fill-rule="evenodd" d="M16.704 4.153a.75.75 0 01.143 1.052l-8 10.5a.75.75 0 01-1.127.075l-4.5-4.5a.75.75 0 011.06-1.06l3.894 3.893 7.48-9.817a.75.75 0 011.05-.143z" clip-rule="evenodd" />
                    </svg>
                    {feature}
                  </li>
                {/each}
              </ul>
            </div>
            <!-- Pro Plan -->
            <div class="rounded-3xl p-8 ring-1 ring-white/10 xl:p-10">
              <div class="flex items-center justify-between gap-x-4">
                <h3 id="tier-pro" class="text-lg font-semibold leading-8 text-white">Pro</h3>
              </div>
              <p class="mt-4 text-sm leading-6 text-gray-300">All-in-one solution to maximize your client growth.</p>
              <p class="mt-6 flex items-baseline gap-x-1">
                <!-- Dynamic Price -->
                <span class="text-4xl font-bold tracking-tight text-white">{getPrice('enterprise')}</span>
                <!-- Dynamic Frequency Label -->
                <span class="text-sm font-semibold leading-6 text-gray-300">{getFrequencyLabel()}</span>
              </p>
              <a href="#" aria-describedby="tier-pro" class="mt-6 block rounded-md bg-white/10 px-3 py-2 text-center text-sm font-semibold leading-6 text-white hover:bg-white/20 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-white">Buy Plan</a>
              <ul role="list" class="mt-8 space-y-3 text-sm leading-6 text-gray-300 xl:mt-10">
                {#each pricingPlans.enterprise.features as feature}
                  <li class="flex gap-x-3">
                    <svg class="h-6 w-5 flex-none text-white" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
                      <path fill-rule="evenodd" d="M16.704 4.153a.75.75 0 01.143 1.052l-8 10.5a.75.75 0 01-1.127.075l-4.5-4.5a.75.75 0 011.06-1.06l3.894 3.893 7.48-9.817a.75.75 0 011.05-.143z" clip-rule="evenodd" />
                    </svg>
                    {feature}
                  </li>
                {/each}
              </ul>
            </div>
          </div>
        </div>
      </div>
      
  
      <!-- CTA Section -->
      <div id="cta" class="relative isolate mt-32 px-6 py-32 sm:mt-56 sm:py-40 lg:px-8">
        <!-- Background SVG Patterns -->
        <svg class="absolute inset-0 -z-10 h-full w-full stroke-white/10 [mask-image:radial-gradient(100%_100%_at_top_right,white,transparent)]" aria-hidden="true">
          <defs>
            <pattern id="cta-pattern" width="200" height="200" x="50%" y="0" patternUnits="userSpaceOnUse">
              <path d="M.5 200V.5H200" fill="none" />
            </pattern>
          </defs>
          <svg x="50%" y="0" class="overflow-visible fill-gray-800/20">
            <path d="M-200 0h201v201h-201Z M600 0h201v201h-201Z M-400 600h201v201h-201Z M200 800h201v201h-201Z" stroke-width="0" />
          </svg>
          <rect width="100%" height="100%" stroke-width="0" fill="url(#cta-pattern)" />
        </svg>
        <div class="absolute inset-x-0 top-10 -z-10 flex transform-gpu justify-center overflow-hidden blur-3xl" aria-hidden="true">
          <div
            class="aspect-[1108/632] w-[69.25rem] flex-none bg-gradient-to-r from-[#80caff] to-[#4f46e5] opacity-20"
            style="clip-path: polygon(73.6% 51.7%, 91.7% 11.8%, 100% 46.4%, 97.4% 82.2%, 92.5% 84.9%, 75.7% 64%, 55.3% 47.5%, 46.5% 49.4%, 45% 62.9%, 50.3% 87.2%, 21.3% 64.1%, 0.1% 100%, 5.4% 51.1%, 21.4% 63.9%, 58.9% 0.2%, 73.6% 51.7%)"
          ></div>
        </div>
        <div class="mx-auto max-w-2xl text-center">
          <h2 class="text-3xl font-bold tracking-tight text-white sm:text-4xl">
            Boost Your Productivity.<br />
            Start Using Koldleads Today.
          </h2>
          <p class="mx-auto mt-6 max-w-xl text-lg leading-8 text-gray-300">
            Discover how Koldleads can transform your agency by providing the tools and data you need to secure more clients and grow your business.
          </p>
          <div class="mt-10 flex items-center justify-center gap-x-6">
            <a href="#pricing" class="rounded-md bg-white px-3.5 py-2.5 text-sm font-semibold text-gray-900 shadow-sm hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-indigo-600 focus:ring-offset-2">Start Trial</a>
            <a href="#features" class="text-sm font-semibold leading-6 text-white">Learn More <span aria-hidden="true">→</span></a>
          </div>
        </div>
      </div>
    </main>
  
    <!-- Footer -->
    <footer aria-labelledby="footer-heading" class="relative">
      <h2 id="footer-heading" class="sr-only">Footer</h2>
      <div class="mx-auto max-w-7xl px-6 pb-8 pt-4 lg:px-8">
        <div class="border-t border-white/10 pt-8 md:flex md:items-center md:justify-between">
          <div class="flex space-x-6 md:order-2">
            <a href="#" class="text-gray-500 hover:text-gray-400">
              <span class="sr-only">Facebook</span>
              <svg class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                <path fill-rule="evenodd" d="M22 12c0-5.523-4.477-10-10-10S2 6.477 2 12c0 4.991 3.657 9.128 8.438 9.878v-6.987h-2.54V12h2.54V9.797c0-2.506 1.492-3.89 3.777-3.89 1.094 0 2.238.195 2.238.195v2.46h-1.26c-1.243 0-1.63.771-1.63 1.562V12h2.773l-.443 2.89h-2.33v6.988C18.343 21.128 22 16.991 22 12z" clip-rule="evenodd" />
              </svg>
            </a>
            <a href="#" class="text-gray-500 hover:text-gray-400">
              <span class="sr-only">Instagram</span>
              <svg class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                <path fill-rule="evenodd" d="M12.315 2c2.43 0 2.784.013 3.808.06 1.064.049 1.791.218 2.427.465a4.902 4.902 0 011.772 1.153 4.902 4.902 0 011.153 1.772c.247.636.416 1.363.465 2.427.048 1.067.06 1.407.06 4.123v.08c0 2.643-.012 2.987-.06 4.043-.049 1.064-.218 1.791-.465 2.427a4.902 4.902 0 01-1.153 1.772 4.902 4.902 0 01-1.772 1.153c-.636.247-1.363.416-2.427.465-1.067.048-1.407.06-4.123.06h-.08c-2.643 0-2.987-.012-4.043-.06-1.064-.049-1.791-.218-2.427-.465a4.902 4.902 0 01-1.772-1.153 4.902 4.902 0 01-1.153-1.772c-.247-.636-.416-1.363-.465-2.427-.047-1.024-.06-1.379-.06-3.808v-.63c0-2.43.013-2.784.06-3.808.049-1.064.218-1.791.465-2.427a4.902 4.902 0 011.153-1.772A4.902 4.902 0 015.45 2.525c.636-.247 1.363-.416 2.427-.465C8.901 2.013 9.256 2 11.685 2h.63zm-.081 1.802h-.468c-2.456 0-2.784.011-3.807.058-.975.045-1.504.207-1.857.344-.467.182-.8.398-1.15.748-.35.35-.566.683-.748 1.15-.137.353-.3.882-.344 1.857-.047 1.023-.058 1.351-.058 3.807v.468c0 2.456.011 2.784.058 3.807.045.975.207 1.504.344 1.857.182.466.399.8.748 1.15.35.35.683.566 1.15.748.353.137.882.3 1.857.344 1.054.048 1.37.058 4.041.058h.08c2.597 0 2.917-.01 3.96-.058.976-.045 1.505-.207 1.858-.344.466-.182.8-.398 1.15-.748.35-.35.566-.683.748-1.15.137-.353.3-.882.344-1.857.048-1.055.058-1.37.058-4.041v-.08c0-2.597-.01-2.917-.058-3.96-.045-.976-.207-1.505-.344-1.858a3.097 3.097 0 00-.748-1.15 3.098 3.098 0 00-1.15-.748c-.353-.137-.882-.3-1.857-.344-1.023-.047-1.351-.058-3.807-.058zM12 6.865a5.135 5.135 0 110 10.27 5.135 5.135 0 010-10.27zm0 1.802a3.333 3.333 0 100 6.666 3.333 3.333 0 000-6.666zm5.338-3.205a1.2 1.2 0 110 2.4 1.2 1.2 0 010-2.4z" clip-rule="evenodd" />
              </svg>
            </a>
            <a href="#" class="text-gray-500 hover:text-gray-400">
              <span class="sr-only">YouTube</span>
              <svg class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                <path
                  fill-rule="evenodd"
                  d="M19.812 5.418c.861.23 1.538.907 1.768 1.768C21.998 8.746 22 12 22 12s0 3.255-.418 4.814a2.504 2.504 0 01-1.768 1.768c-1.56.419-7.814.419-7.814.419s-6.255 0-7.814-.419a2.505 2.505 0 01-1.768-1.768C2 15.255 2 12 2 12s0-3.255.417-4.814a2.507 2.507 0 011.768-1.768C5.744 5 11.998 5 11.998 5s6.255 0 7.814.418ZM15.194 12 10 15V9l5.194 3Z"
                  clip-rule="evenodd"
                />
              </svg>
            </a>
          </div>
          <p class="mt-8 text-xs leading-5 text-gray-400 md:order-1 md:mt-0">&copy; 2024 Koldleads, Inc. All rights reserved.</p>
        </div>
      </div>
    </footer>
  </div>
  