<script>
  import axios from "axios";
  import LeftArrowIcon from "../../components/icons/LeftArrowIcon.svelte";

  let email = "";
  let password = "";
  let loading = false;

  const handleSubmit = async () => {
    try {
      if (password.length >= 8) {
        loading = true;
        const response = await axios.post("http://dummyjson.com/users/add", {
          email,
          password,
        });
        console.log(response.data);
      } else {
        alert("sifre minimum 8 karakter olmalidir");
      }
    } catch (error) {
      console.warn("error: ", error);
    }
  };
</script>

<div
  class="md:absolute max-md:h-[100vh] top-0 z-[999999] right-0 left-0 bottom-0 overflow-hidden bg-gray-300"
>
  <a
    href="/"
    class="absolute max-md:hidden left-4 z-[9999999] top-4 bg-white py-2 px-6 rounded-lg bg-opacity-55 hover:bg-opacity-100"
  >
    <LeftArrowIcon />
  </a>
  <div
    class="relative flex flex-wrap lg:h-screen lg:items-center max-md:flex max-md:items-center max-md:justify-center max-md:h-[80%]"
  >
    <div class="w-full px-4 py-12 sm:px-6 sm:py-16 lg:w-1/2 lg:px-8 lg:py-24">
      <div class="mx-auto max-w-lg text-center">
        <h1 class="h1 font-bold">Daxil ol</h1>

        <p class="mt-4 text-gray-500">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Et libero
          nulla eaque error neque ipsa culpa autem, at itaque nostrum!
        </p>
      </div>

      <form
        on:submit|preventDefault={handleSubmit}
        class="mx-auto mb-0 mt-8 max-w-md space-y-4"
      >
        <div>
          <label for="email" class="sr-only">Email</label>

          <div class="relative">
            <input
              type="email"
              bind:value={email}
              required
              class="w-full rounded-lg border-gray-200 p-4 pe-12 text-sm shadow-sm focus:ring-[--primary-color] focus:border-[--primary-color]"
              placeholder="Email"
            />
          </div>
        </div>

        <div>
          <label for="password" class="sr-only">Password</label>

          <div class="relative">
            <input
              type="password"
              bind:value={password}
              required
              class="w-full rounded-lg border-gray-200 p-4 pe-12 text-sm shadow-sm focus:ring-[--primary-color] focus:border-[--primary-color]"
              placeholder="Şifrə"
            />
          </div>
        </div>

        <div class="flex items-center justify-between">
          <p class="text-sm text-gray-500">
            Hesabınız yoxdur?
            <a class="underline" href="/sign-up">Hesab yaradın</a>
          </p>

          <button
            type="submit"
            class="inline-block rounded-lg bg-black px-5 py-3 text-sm font-medium text-white"
          >
            Daxil ol
          </button>
        </div>
      </form>
    </div>

    <div class="relative h-64 w-full sm:h-96 lg:h-full lg:w-1/2 max-md:hidden">
      <img
        alt=""
        src="https://images.unsplash.com/photo-1630450202872-e0829c9d6172?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=774&q=80"
        class="absolute inset-0 h-full w-full object-cover"
      />
    </div>
  </div>
</div>
