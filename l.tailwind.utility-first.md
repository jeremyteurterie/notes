---
id: 9uenotxv5hfczgmrovb2jow
title: Utility First
desc: ''
updated: 1689302906708
created: 1689302155207
---
# Utility First

[PREVIEW](http://127.0.0.1:5500/devlog/learning-area/tailwindcss/bradtraversy/tailwind-sandbox/tailwind-sandbox-done/04-typography/index.html)

```
      .alert {
        display: flex;
        max-width: 24rem;
        margin: 0 auto;
        padding: 1.5rem;
        border-radius: 0.5rem;
        background-color: #fff;
        box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1),
          0 10px 10px -5px rgba(0, 0, 0, 0.04);
      }
      .alert-logo-wrap {
        flex-shrink: 0;
      }
      .alert-logo {
        height: 3rem;
        width: 3rem;
      }
      .alert-body {
        margin-left: 1.5rem;
        padding-top: 0.25rem;
      }
      .alert-title {
        color: #1a202c;
        font-size: 1.25rem;
        line-height: 1.25;
        font-weight: 500;
      }
      .alert-message {
        color: #718096;
        font-size: 1rem;
        line-height: 1.5;
      }

```      
    <!-- HTML/CSS Version -->
    <div class="alert">
      <div class="alert-logo-wrap">
        <img class="alert-logo" src="../assets/img/warning.svg" alt="alert" />
      </div>
      <div class="alert-body">
        <h4 class="alert-title">Are You Sure?</h4>
        <p class="alert-message">You are about to delete a post</p>
      </div>
    </div>

    <!-- Tailwind Version -->
    <div class="flex items-center p-6 max-w-sm mx-auto bg-white rounded-xl shadow-lg space-x-4">
      <img class="h-12 w-12" src="../assets/img/warning.svg" alt="alert" />
      <div>
        <div class="text-xl font-medium text-black">Are You Sure?</div>
        <p class="text-slate-500">You are about to delete a post</p>
      </div>
    </div>
  </body>
</html>

<!--  
  - We didn't have to write any extra CSS
  - No spending time on class names
  - No worrying about our CSS file getting too large
  - Add and change things on the fly, try different layouts, etc
  - Less chance of stuff going wrong
-->

[LIVE](http://127.0.0.1:5500/devlog/learning-area/tailwindcss/bradtraversy/tailwind-sandbox/tailwind-sandbox-done/04-typography/index.html)