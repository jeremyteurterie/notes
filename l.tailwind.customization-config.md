---
id: ujofn2wjcr4msxb0rsias4o
title: Customization Config
desc: ''
updated: 1689304470962
created: 1689303277823
---
# Customization & Config

[PREVIEW](http://127.0.0.1:5500/devlog/learning-area/tailwindcss/bradtraversy/tailwind-sandbox/tailwind-sandbox-done/17-customization/index.html)

```
 tailwind.config = {
        theme: {
          screens: {
            sm: '550px',
            md: '800px',
            lg: '1200px',
            xl: '1440px',
          },
          fontFamily: {
            sans: ['Graphik', 'sans-serif'],
            serif: ['Merriweather', 'serif'],
          },
          extend: {
            colors: {
              primary: '#ff5733',
              secondary: '#fffc33',
            },
            spacing: {
              6: '2.5rem',
              128: '32rem',
            },
            borderRadius: {
              '4xl': '2rem',
            },
          },
        },
      }
    </script>
    <title>Customization</title>
  </head>
  <body
    class="bg-black sm:bg-green-800 md:bg-blue-800 lg:bg-yellow-800 xl:bg-purple-800 2xl:bg-orange-800"
  >
    <div
      class="border-secondary border p-6 mb-128 max-w-sm mx-auto rounded-4xl"
    >
      <h1 class="text-primary text-xl"></h1>
    </div>

    <script>
      function showBrowserWidth() {
        const width = window.innerWidth

        document.querySelector('h1').innerHTML = `Width: ${width}`
      }

      window.onload = showBrowserWidth
      window.onresize = showBrowserWidth
    </script>
  </body>
</html>

<!-- Breakpoint Classes
    sm	640px	  @media (min-width: 640px) { ... }
    md	768px	  @media (min-width: 768px) { ... }
    lg	1024px	@media (min-width: 1024px) { ... }
    xl	1280px	@media (min-width: 1280px) { ... }
    2xl	1536px	@media (min-width: 1536px) { ... }
  -->
```