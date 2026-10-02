# Website maintenance boundaries

GitHub Pages publishes `main` at https://feltfolio.app/. A push to another branch
is not a live deployment. Preserve CNAME and .nojekyll.

Styling the homepage is independent of authentication. Preserve #terms, #privacy,
and #purchases anchors, readable legal/support links, keyboard focus, sufficient
contrast, zoom/reflow and screen-reader structure. Do not silently change legal
text: the app serves separately versioned documents from Supabase.

Treat auth/confirm/index.html and crew/join/index.html as security-sensitive.
Keep token parsing, history cleanup, no-referrer, noindex, CSP and explicit-action
behavior intact. Do not add analytics, third-party scripts, external fonts or
logging to token pages. Inline script edits require updating the CSP hash and
rerunning the respective tests in FeltFolio/tools/security/ in the app repo.

Preserve .well-known/apple-app-site-association, including auth paths, Crew path,
app ID and webcredentials. Test it from the live HTTPS site without redirects.
Never rename invite/auth URLs as part of a visual redesign.

robots.txt intentionally permits fetching pages so crawlers can see noindex on
auth/invite pages. It is not access control. The sitemap lists only public content,
not token pages or fragment anchors. Favicons, apple-touch-icon, CNAME and
.nojekyll already exist; a web-app manifest is not needed for this non-PWA site.
