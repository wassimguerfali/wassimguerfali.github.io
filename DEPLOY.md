# Getting wassimguerfali.com live — ~30 minutes, ~$10/year

## 1. Buy the domain (~$10.44/yr)

Cloudflare Registrar sells .com at wholesale with no first-year discount trick and free WHOIS
privacy. Sign up at dash.cloudflare.com → Domain Registration → Register Domain → search
`wassimguerfali.com`.

If it's taken, fallbacks in order of preference: `wassimguerfali.net`, `wguerfali.com`,
`wassim-guerfali.com`. Avoid `.io`, `.xyz`, `.me` — econ readers read those as a personal blog,
not a researcher page.

## 2. Put the site on GitHub Pages (free)

1. Create a GitHub account if you don't have one. Use a professional username — `wassimguerfali`
   if it's free. This URL will end up on your CV.
2. Create a **public** repo named exactly `wassimguerfali.github.io`.
3. Upload three files to the root of that repo:
   - `index.html` (this site — your headshot is embedded inside it, no separate image needed)
   - `cv.pdf` (your CV)
   - `CNAME` (a plain text file containing one line: `wassimguerfali.com`)
   - `sitemap.xml` and `robots.txt` (these tell Google what to index — see step 5)
4. Repo → Settings → Pages → Source: `Deploy from a branch`, branch `main`, folder `/ (root)`.
5. Wait ~2 minutes. `https://wassimguerfali.github.io` should load.

## 3. Point the domain at it

In Cloudflare → your domain → DNS → add these records:

| Type  | Name | Content                    | Proxy |
|-------|------|----------------------------|-------|
| A     | @    | 185.199.108.153            | DNS only |
| A     | @    | 185.199.109.153            | DNS only |
| A     | @    | 185.199.110.153            | DNS only |
| A     | @    | 185.199.111.153            | DNS only |
| CNAME | www  | wassimguerfali.github.io   | DNS only |

Set proxy to **DNS only** (grey cloud) at first — orange-cloud proxying fights GitHub's
certificate issuance. You can turn it on later once HTTPS works.

Then in GitHub → Settings → Pages → Custom domain → enter `wassimguerfali.com` → Save →
tick **Enforce HTTPS** once the certificate provisions (can take up to an hour).

## 4. Free email at your domain

Cloudflare → Email → Email Routing → add `hello@wassimguerfali.com` forwarding to your Gmail.
Costs nothing. Then set Gmail to "send mail as" that address (Settings → Accounts → Add another
email address) so replies come from the domain, not `wassimguerfali3@gmail.com`.

## 5. Getting it to show up on Google

Google does not host websites — it only indexes ones that already exist. So this step comes *after*
steps 1–3, not instead of them. Nothing below works until the site is live.

1. Go to **search.google.com/search-console** and sign in with your Google account.
2. Click **Add property** → choose the **Domain** option (left box) → enter `wassimguerfali.com`.
3. Google gives you a TXT record. In Cloudflare → DNS → Add record: Type `TXT`, Name `@`,
   Content = the string Google gave you. Save, then click **Verify** in Search Console.
   (If it fails, wait ten minutes for DNS to propagate and click Verify again.)
4. In Search Console → **Sitemaps** → enter `sitemap.xml` → Submit.
5. In Search Console → **URL Inspection** → paste `https://wassimguerfali.com` →
   **Request Indexing**. This pushes you to the front of the queue.

Expect **a few days to two weeks** before you appear. Your name is uncommon enough that once
indexed you should rank first for "Wassim Guerfali" without any further work — the site already
carries structured Person data telling Google who you are, where you study, and what you research.

Two things that speed it up more than anything technical: put the URL on your **LinkedIn profile**
(a real inbound link Google crawls constantly) and on your **Alma College** profile page if the
department has one. Backlinks from established domains are what actually move indexing.

## Before you publish — checklist

- [ ] Skim `cv.pdf` — it is built from your real resume, reorganized as an academic CV (research above
      awards, skills on page 1). Check that nothing was lost in the reordering.
- [ ] Rewrite the Act 51 abstract in your own voice once the draft firms up
- [ ] Confirm Dr. Hinkel and Larissa Petrucci are OK being named on a public page for the Santa Clara study
- [ ] Delete every `<div class="todo">...</div>` block in `index.html` (they render as visible orange notes)
- [ ] Add the Michigan Academy presentation to both the site and the CV **once it is accepted** — not before
- [ ] Add the site URL to your LinkedIn profile, your email signature, and the header of your CV

## Deliberately not on this site

**GPA.** Your economics GPA is excellent and belongs on your CV where the reader also sees the
coursework that produced it. A number sitting alone on a webpage invites the cumulative question
and answers nothing a transcript won't. Applications ask for it; websites shouldn't volunteer it.

**Data or findings from Santa Clara.** The eCPR records are confidential and the paper is
co-authored. Title, question, and your role only until it's published.

**A blog.** An empty or three-post blog reads worse than none. Skip it until you have something
you'd defend in a seminar.

**GitHub.** No link, because you don't have a repo worth linking yet. When the Act 51 parser is cleaned
up and the confidential inputs are stripped out, a public repo of that pipeline is the single highest-value
thing you could add to this site for a pre-doc reader. Add the link then.
