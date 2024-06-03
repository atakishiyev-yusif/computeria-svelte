<script>
  import axios from "axios";
  import { goto } from "$app/navigation";
  import Logo from "../../components/Logo.svelte";
  import Loader from "../../components/Loader.svelte";
  import LeftArrowIcon from "../../components/icons/LeftArrowIcon.svelte";

  let firstName = "";
  let lastName = "";
  let email = "";
  let password = "";
  let passwordConfirmation = "";
  let loading = false;

  const handleSubmit = async () => {
    try {
      if (passwordConfirmation === password) {
        if (password.length >= 8) {
          loading = true;
          const response = await axios.post("http://dummyjson.com/users/add", {
            firstName,
            lastName,
            email,
            password,
          });
          console.log("form gonderildi", response.data);
          goto("/about");
        } else {
          alert("sifre minimum 8 karakter olmalidir.");
        }
      } else {
        alert("Sifreler ferqlidir");
      }
    } catch (error) {
      console.log(error);
    } finally {
      loading = false;
    }
  };
</script>

{#if loading}
  <Loader />
{/if}

<a
  href="/"
  class="absolute left-4 z-[9999999] top-4 bg-white py-2 px-6 rounded-lg bg-opacity-55 hover:bg-opacity-100"
>
  <LeftArrowIcon />
</a>

<section
  class="bg-white absolute top-0 z-[999999] right-0 left-0 bottom-0 h-[120vh] max-md:h-[140vh] overflow-hidden"
>
  <div class="lg:grid lg:min-h-screen lg:grid-cols-12">
    <section
      class="relative flex h-32 items-end bg-gray-900 lg:col-span-5 lg:h-full xl:col-span-6"
    >
      <img
        alt=""
        src="https://bestinau.com.au/wp-content/uploads/2019/09/Best-Computer-Stores-in-Canberra.jpg"
        class="absolute inset-0 h-full w-full object-cover opacity-30"
      />

      <div class="hidden lg:relative lg:block lg:p-12">
        <a class="block text-white" href="#">
          <Logo />
        </a>

        <h2 class="mt-6 text-2xl font-bold text-white sm:text-3xl md:text-4xl">
          Welcome to Computeria
        </h2>

        <p class="mt-4 leading-relaxed text-white/90">
          Lorem, ipsum dolor sit amet consectetur adipisicing elit. Eligendi nam
          dolorum aliquam, quibusdam aperiam voluptatum.
        </p>
      </div>
    </section>

    <main
      class=" flex items-center justify-center px-8 py-8 sm:px-12 lg:col-span-7 lg:px-16 lg:py-12 xl:col-span-6"
    >
      <div class="max-w-xl lg:max-w-3xl">
        <div class="relative -mt-16 block lg:hidden">
          <a
            class="inline-flex size-16 items-center justify-center rounded-full bg-white text-blue-600 sm:size-20"
            href="#"
          >
            <span class="sr-only">Əsas səhifə</span>
            <Logo />
          </a>

          <h1
            class="mt-2 text-2xl font-bold text-gray-900 sm:text-3xl md:text-4xl"
          >
            Welcome to Computeria
          </h1>

          <p class="mt-4 leading-relaxed text-gray-500">
            Lorem, ipsum dolor sit amet consectetur adipisicing elit. Eligendi
            nam dolorum aliquam, quibusdam aperiam voluptatum.
          </p>
        </div>

        <form
          on:submit|preventDefault={handleSubmit}
          class="mt-8 grid grid-cols-6 gap-6"
        >
          <div class="col-span-6 sm:col-span-3">
            <label
              for="FirstName"
              class="block text-sm font-medium text-gray-700"
            >
              Ad
            </label>

            <input
              type="text"
              placeholder="John"
              id="FirstName"
              name="first_name"
              bind:value={firstName}
              required
              class="mt-1 w-full rounded-md border-gray-200 bg-white text-sm text-gray-700 shadow-sm"
            />
          </div>

          <div class="col-span-6 sm:col-span-3">
            <label
              for="LastName"
              class="block text-sm font-medium text-gray-700"
            >
              Soyad
            </label>

            <input
              type="text"
              id="LastName"
              name="last_name"
              placeholder="Doe"
              bind:value={lastName}
              required
              class="mt-1 w-full rounded-md border-gray-200 bg-white text-sm text-gray-700 shadow-sm"
            />
          </div>

          <div class="col-span-6">
            <label for="Email" class="block text-sm font-medium text-gray-700">
              Email
            </label>

            <input
              type="email"
              id="Email"
              name="email"
              placeholder="example@mail.com"
              bind:value={email}
              required
              class="mt-1 w-full rounded-md border-gray-200 bg-white text-sm text-gray-700 shadow-sm"
            />
          </div>

          <div class="col-span-6 sm:col-span-3">
            <label
              for="Password"
              class="block text-sm font-medium text-gray-700"
            >
              Şifrə
            </label>

            <input
              type="password"
              id="Password"
              name="password"
              placeholder="min: 8 character"
              bind:value={password}
              required
              class="mt-1 w-full rounded-md border-gray-200 bg-white text-sm text-gray-700 shadow-sm"
            />
          </div>

          <div class="col-span-6 sm:col-span-3">
            <label
              for="PasswordConfirmation"
              class="block text-sm font-medium text-gray-700"
            >
              Şifrəni təsdiqlə
            </label>

            <input
              type="password"
              id="PasswordConfirmation"
              name="password_confirmation"
              placeholder="min: 8 character"
              bind:value={passwordConfirmation}
              required
              class="mt-1 w-full rounded-md border-gray-200 bg-white text-sm text-gray-700 shadow-sm"
            />
          </div>

          <div class="col-span-6">
            <p class="text-sm text-gray-500 max-w-[45ch]">
              Qeydiyyatdan keçərək Computeria-nın
              <a href="/user-agreement" class="text-gray-700 underline text-sm">
                İstifadəçi razılaşması
              </a>
              və
              <a href="/privacy-policy" class="text-gray-700 underline text-sm">
                Məxfilik siyasəti
              </a>
              ilə razılaşıram
            </p>
          </div>

          <div class="col-span-6 sm:flex sm:items-center sm:gap-4">
            <button
              type="submit"
              class="inline-block shrink-0 rounded-md border border-black bg-black px-12 py-3 text-sm font-medium text-white transition hover:bg-transparent hover:text-black focus:outline-none focus:ring active:text-black"
            >
              Hesab yarat
            </button>

            <p class="mt-4 text-sm text-gray-500 sm:mt-0">
              Artıq bir hesabınız var?
              <a href="/login" class="text-gray-700 underline text-sm"
                >Daxil ol</a
              >.
            </p>
          </div>
        </form>
      </div>
    </main>
  </div>
</section>
