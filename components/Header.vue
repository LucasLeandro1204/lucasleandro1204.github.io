<template>
  <header id="home" class="pt-28 sm:pt-32">
    <nav
      :class="fixed ? 'py-4 shadow-lg' : 'py-8'"
      class="transition-lg w-full fixed z-20 pin-t pin-l bg-secondary-darker px-8">

      <div class="max-w-xl mx-auto flex justify-between">
        <img
          alt="Avatar"
          src="/me.jpg"
          class="transition rounded-full w-8 h-8"
          :class="fixed ? 'sm:w-8 sm:h-8' : 'sm:w-12 sm:h-12'"
          >

        <ul class="list-reset flex text-sm items-center">
          <li
            :key="anchor"
            class="ml-6 font-thin"
            v-for="(label, anchor) in links"
            >
            <a class="text-white hover:text-primary transition" :href="anchor" v-text="label"></a>
          </li>
        </ul>
      </div>
    </nav>

    <div class="max-w-xl text-white mx-auto">
      <h1 class="text-6xl mb-6">Lucas Leandro</h1>

      <div class="flex mb-8 items-center">
        <a
          href="mailto:lucasleandro1204@gmail.com?subject=From Website: Hello Lucas"
          class="text-primary border border-primary rounded font-bold text-sm px-4 sm:px-6 py-3 transition hover:text-white hover:bg-primary"
          >
          GET IN TOUCH
        </a>

        <nav class="ml-8">
          <ul class="flex list-reset">
            <li
              class="mr-3"
              :key="anchor"
              v-for="(icon, anchor) in social"
              >

              <a
                :href="anchor"
                target="_blank"
                class="w-4 block text-white transition hover:text-primary"
                >
                <Component class="fill-current" :is="icon" />
              </a>
            </li>
          </ul>
        </nav>
      </div>

      <p class="text-sm sm:text-base leading-loose sm:leading-normal">My name Is Lucas Leandro, I'm a Full Stack Developer from Florianópolis, Santa Catarina - Brazil.</p>
      <p class="text-sm sm:text-base leading-loose sm:leading-normal mb-4 text-primary">I solve problems.</p>
      <p class="text-sm sm:text-base leading-loose sm:leading-normal mb-4">At Front-end I work with <span class="text-primary">Vue</span> and <span class="text-primary">React</span>, I do make use of css preprocessors like <span class="text-primary">SCSS</span>. For static websites I use <span class="text-primary">Nuxt</span>.</p>
      <p class="text-sm sm:text-base leading-loose sm:leading-normal">My Back-end stack is primarily PHP (<span class="text-primary">Laravel</span>, Codeigniter perhaps), but I also work with <span class="text-primary">Node</span> (<span class="text-primary">Express</span>, Koa, Adonis). I do have experience with relational databases (<span class="text-primary">MySQL</span>) and NoSQL (<span class="text-primary">MongoDB</span>). I write <span class="text-primary">tests</span> for every project, they help me preventing bugs, and keeping the application stable as it grows.</p>
    </div>
  </header>
</template>

<script>
  import IconMail from '~/assets/icon/mail.svg';
  import IconGitHub from '~/assets/icon/github.svg';
  import IconTwitter from '~/assets/icon/twitter.svg';
  import IconLinkedin from '~/assets/icon/linkedin.svg';

  export default {
    mounted () {
      const listener = () => {
        this.fixed = window.scrollY > 0;
      };

      window.addEventListener('scroll', listener, false);

      this.$once('hook:beforeDestroy', () => {
        window.removeEventListener('scroll', listener, false);
      });
    },

    data: () => ({
      fixed: false,
    }),

    computed: {
      links: () => ({
        '#home': 'HOME',
        '#projects': 'PROJECTS',
        'mailto:lucasleandro1204@gmail.com?subject=From Website: Hello Lucas': 'GET IN TOUCH',
      }),

      social: () => ({
        'https://github.com/lucasleandro1204': IconGitHub,
        'https://twitter.com/lucasleandro412': IconTwitter,
        'https://www.linkedin.com/in/lucasleandro1204/': IconLinkedin,
        'mailto:lucasleandro1204@gmail.com?subject=From Website: Hello Lucas': IconMail,
      }),
    },
  };
</script>
