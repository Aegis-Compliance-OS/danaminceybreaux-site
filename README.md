# danaminceybreaux.com — Site Rebuild
Personal hub site for Dana Mincey-Breaux. Static HTML/CSS/JS, no build process required.

## File Structure
```
/
├── index.html          ← Homepage
├── about.html          ← Bio, credentials, contact
├── aegis.html          ← Aegis Compliance OS
├── fenix.html          ← Fenix Capital
├── trident.html        ← Project TRIDENT
├── engagements.html    ← Speaking & events
├── css/
│   └── style.css       ← All styles
├── js/
│   └── main.js         ← Nav, scroll reveal, clock
└── assets/             ← Place images here
    └── (your headshot, logos, etc.)
```

## GitHub Pages Deployment (Terminal)

### 1. Create the repo
```bash
# In GitHub: create new repo named "danaminceybreaux-site" (public)
# Then locally:
cd ~/Desktop  # or wherever you want to work
git clone https://github.com/YOUR_USERNAME/danaminceybreaux-site.git
cd danaminceybreaux-site
```

### 2. Copy site files into the repo
```bash
# Copy everything from the downloaded site folder into the repo root
cp -r /path/to/downloaded/site/* .
```

### 3. Push to GitHub
```bash
git add .
git commit -m "Initial site build"
git push origin main
```

### 4. Enable GitHub Pages
- Go to repo → Settings → Pages
- Source: Deploy from branch → main → / (root)
- Save

### 5. Point danaminceybreaux.com DNS to GitHub Pages
In your domain registrar (Netlify DNS or wherever danaminceybreaux.com is managed):

Add these 4 A records:
```
@ → 185.199.108.153
@ → 185.199.109.153
@ → 185.199.110.153
@ → 185.199.111.153
```

Add 1 CNAME record:
```
www → YOUR_USERNAME.github.io
```

Then in GitHub Pages settings → Custom domain → enter: danaminceybreaux.com
Check "Enforce HTTPS" once DNS propagates (~10 min to 48 hrs).

### 6. Fix logo image path (after adding your logo)
Place your logo at `assets/logo.png` then update any `<img src>` tags if added.

## Adding Future Engagements
Open `engagements.html` and add a new `<tr>` row to the table:
```html
<tr>
  <td class="et-date">Month DD, 2026</td>
  <td>
    <div class="et-event">Event Name</div>
    <div class="et-org">Organization · Location</div>
  </td>
  <td class="et-role">Your Role</td>
  <td><span class="et-badge upcoming">Upcoming</span></td>
</tr>
```
Change `upcoming` to `completed` or `speaker` after the event.

## Migrating from Netlify
1. In Netlify dashboard → Site settings → Domain management
2. Remove the custom domain `danaminceybreaux.com` from Netlify
3. Update DNS A records to point to GitHub Pages IPs above
4. Your Netlify site can stay live until DNS propagates to GitHub Pages
