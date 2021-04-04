# sveltekit-bugrepo1

1) mkdir my-app
2) cd my-app
3) npm init svelte@next
4) npm install
5) create `/src/routes/test`:
```
export async function get() {
  return { body: {} }
};
```
6) modify the `src/routes/index.svelte`:
```
<p>Visit <a href="/test">/test</a> to see the problem.</p>
```

7) npm run dev - visit the homepage, open js console, click /test, notice debugger:
```
Uncaught (in promise) TypeError: Cannot read property 'nodes' of undefined
    at Renderer.update (start.js:497)
    at async Router._navigate (start.js:248)
```
coming from: `.svelte/dev/runtime/internal/start.js`