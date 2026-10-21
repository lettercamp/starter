# Good Company · Lettercamp starter

A fictional software company blog built with Lettercamp. Good Company makes Good Product, a shared workspace for team updates, decisions, and handoffs. Includes twelve complete sample posts: four each in Company, Product, and Engineering, with original grayscale cover illustrations and illustrated author portraits.

The company, product, people, release timeline, and engineering accounts are fictional demonstration content. There is no live Good Product service or sign-up destination. Replace the sample identity and claims before using the starter for your own company.

## Preview locally

With Node.js 22.19 or newer installed, run this from the publication folder:

```sh
npx lettercamp dev
```

If you are developing the CLI in the adjacent `cli` repository, run `npm run dev` there to preview `../test-publication` with automatic restarts. Use `npm run dev -- ../starter` to preview this starter instead.

## Make it yours

Edit `settings.json` for the site name, homepage heading (`homeTitle`), description, navigation, footer, and typography. The homepage is generated automatically. The description is used in page metadata, not displayed below the heading. Articles live directly in `pages/`; each has a category, date, summary, cover image, `author`, and `authorImage` in its frontmatter. The nine newest posts appear at the top; older posts appear in Archive. One or two posts use wide rows, while three or more use the responsive grid. Set `showReadingTime` to `false` in `settings.json` to hide the automatic reading estimates on article pages. Cards show the author and date; Archive shows only the title, author, and date.

The starter includes five footer link columns. Configure up to five with `footer.links`; extra columns are ignored. They adapt to three columns on tablets and two on phones.

Add optional social links with `footer.socials`, a map of platform names to your profile URLs (for example, `x`, `github`, or `linkedin`). Omit it to hide social links. See the configuration reference below for an example.

Editable cover artwork lives in `assets/covers/`, and author artwork lives in `assets/authors/`. The sample covers, portraits, and favicon are hosted at `assets.lettercamp.com`; pages reference their permanent HTTPS URLs. The cover PNGs are 1200 × 630 and are used for article thumbnails and social previews. All sample copy and illustrations are included for customization; Good Company is a demonstration identity, not an affiliated business.

Read the [CLI guide](https://www.lettercamp.com/docs/cli) and [configuration reference](https://www.lettercamp.com/docs/configuration).

## Images

Use absolute HTTPS image URLs in Markdown, page frontmatter, and `settings.json`. Upload images through the Lettercamp web editor or use an existing image host, then paste the returned URL. Images under `public/` are not copied into previews or builds; that folder remains available for non-image static files.
