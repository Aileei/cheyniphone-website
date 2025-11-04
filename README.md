Cheyn iPhones and Gadgets — Static site

This is a small static site for a demo shop. It is built with plain HTML, CSS and vanilla JavaScript and stores cart data in localStorage.

Files of interest
- index.html — product listing / homepage
- product.html — product details, cart overlay and checkout flow
- services.html, location.html, contact.html — supporting pages

Quick local test
1. Open `index.html` in a browser (double-click the file or open via browser "Open File...").
2. Click a product's "Check Out" link to open `product.html?model=...`.
3. On `product.html` use "Add to Cart" to add items, then click the cart icon (top nav) to open the cart overlay.
4. Use Checkout to open the checkout form — submission simulates redirect to Skyro and clears the cart (client-side only).

Publish options
- GitHub Pages (recommended for static sites):
  1. Create a public repository and push this folder's contents to the `main` branch.
  2. In the repo Settings > Pages, select the `main` branch and `/ (root)` folder as the source.
  3. Wait a minute — your site will be available at `https://<username>.github.io/<repo>`.

Automatic deploy via GitHub Actions
I added a GitHub Actions workflow at `.github/workflows/pages-deploy.yml` that will automatically publish your site to GitHub Pages when you push to `main`.

To publish from your local machine (PowerShell commands):
```powershell
# from the project root folder
git init
git add .
git commit -m "Prepare site for publish"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin main
```

After the push completes, GitHub will run the workflow and you should see the Pages deployment in the repository Actions/Pages sections. The site will be available at `https://<your-username>.github.io/<your-repo>` (or the repo's Pages URL shown in Settings → Pages).

- Netlify / Vercel (drag-and-drop or connect repo):
  - Create a Netlify account, drag-and-drop the project folder into "Sites" (no build step required).
  - Or connect your Git repository and deploy. Adjust publish directory to `/`.

Notes & recommendations before going live
- This is a client-side demo only. Real payments and order processing require a backend and secure payment gateway integration.
- Consider centralizing shared scripts/styles into separate files (e.g., `assets/js/cart.js`, `assets/css/site.css`) for maintainability.
- For better reliability, vendor important images (payment logos/product images) locally or use a reliable CDN with onerror fallbacks.
- Add HTTPS hosting (GitHub Pages, Netlify, Vercel provide HTTPS by default).

If you want, I can:
- Create a small `assets/` structure and move shared CSS/JS into it.
- Centralize cart code into a single script and include it on all pages.
- Add a build step (e.g., simple npm script) to minify assets for production.

