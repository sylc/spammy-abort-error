The client is mostly created from a vite react-ts template. \
I have added a useEffect that call a `/api` route on the server on mount and setup vite to proxy the request
to a basic deno server.

To reproduce:
- Run `deno task dev`
- Update the client default state value. 

```diff
diff --git a/client/src/App.tsx b/client/src/App.tsx
index 2136174..1ddfcae 100644
--- a/client/src/App.tsx
+++ b/client/src/App.tsx
@@ -5,7 +5,7 @@ import viteLogo from '/vite.svg'
 import './App.css'

 function App() {
-  const [count, setCount] = useState(10)
+  const [count, setCount] = useState(11)

   useEffect(() => {
     const getData = async () => { await fetch('/api/data') };
```

- see the terminal having multiple Abort error.

- revert to deno version 2.2.5. no abort error in console.
