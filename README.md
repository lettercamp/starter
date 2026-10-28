# Lorem Ipsum Blog · Lettercamp starter

A Lorem Ipsum Blog built with Lettercamp. Includes twelve distinct placeholder posts in Aurora, Serenitas, and Lumina, with varied title, summary, and article lengths, cover images, and author portraits.

The posts use varied lorem ipsum placeholder copy. Replace it with your own writing before publishing your blog.

## Preview locally

With Node.js 22.22 or newer installed, run this from the publication folder:

```sh
npx lettercamp dev
```

If you are developing the CLI in the adjacent `cli` repository, run `npm run dev` there to preview `../test-publication` with automatic restarts. Use `npm run dev -- ../starter` to preview this starter instead.

## Make it yours

Edit `settings.json` for the site name, homepage heading (`home.title`), description, navigation, footer, and typography. Set `header.button.label` and `header.button.href` for the header button, and `header.button.color` to a six-digit hex background color (default `#111111`). Button text automatically uses black or white for contrast. Set `header.button` to `null` to hide it. The homepage is generated automatically. The description appears below the homepage heading and in page metadata. Articles live directly in `pages/`; each has a category, date, summary, cover image, an ordered `authors` array in its frontmatter (each entry has a `name` and optional `image` URL). The nine newest posts appear at the top; older posts appear in Archive. Choose Grid or Rows with `home.feedLayout`; the selected layout stays the same when filtering categories. Set `post.showReadingTime` to `false` in `settings.json` to hide the automatic reading estimates on article pages. Cards show author names, portraits, and the date; Archive shows only the title, author names, and date. Omit `authors` or set `authors: []` to show no authors. Authors are configured per post; there are no site defaults.

Settings use the same structure in the CLI and web editor: site identity stays at
its root, while `design`, `home`, `post`, `header`, `footer`, `seo`, and `analytics`
group related options. `seo.keywords` is an array of strings. Set
`analytics.googleAnalyticsId` to your GA4 measurement ID, or leave it blank to
disable analytics. Search and social overrides live under `seo`; page frontmatter
continues to use page-specific fields such as `metaTitle` and `ogImage`.

Numeric sizes include units: `design.typography.baseSizePx`,
`home.contentWidthPx`, `post.contentWidthEm`, and `design.imageRadiusPercent`.
`design.typography.bodyLineHeight` is a unitless multiple of text size.

The starter includes four footer link columns. Configure up to four with `footer.columns`; extra columns are ignored. They adapt to three columns on tablets and two on phones. Footer text matches header navigation at 87.5% of `design.typography.baseSizePx` (14px with the default 16px base size).

Add optional social links with `footer.socials`, an ordered array of `{ "platform": "github", "href": "https://github.com/your-org" }` objects. Omit it to hide social links. See the configuration reference below for an example.

Optimized JPEG covers and the original SVG cover artwork live in `assets/covers/`; author artwork lives in `assets/authors/`. The sample covers, portraits, and favicon are hosted at `assets.lettercamp.com`; pages reference their permanent HTTPS URLs. The progressive JPEG covers are 1200 × 630 and are used for article thumbnails and social previews. All sample copy and illustrations are included for customization.

Read the [CLI guide](https://www.lettercamp.com/docs/cli) and [configuration reference](https://www.lettercamp.com/docs/configuration).

## React components

The Maecenas sed diam eget risus article includes a sample reading-time calculator in
`components/ReadingTimeCalculator.jsx`. Enter a word count or choose a preset to
estimate reading time at 200 words per minute. Import it after the frontmatter
in any MDX page:

```mdx
import ReadingTimeCalculator from '../components/ReadingTimeCalculator.jsx';

<ReadingTimeCalculator client:visible initialWords={600} />
```

`client:visible` makes the calculator interactive when it enters the viewport.
Components without a client directive render as static HTML. Lettercamp includes
React. Edit custom MDX in Source mode in the web editor.

See the [React components guide](https://www.lettercamp.com/docs/react-components).

## Custom headers and footers

Add `components/Header.jsx` or `components/Footer.jsx` to replace that region on
every page. `.tsx` works too; use one extension per component and a default export.
Both components receive `{ site, pathname }` and become interactive on page load.
Delete or rename an override to restore the default.

Simple examples live in `examples/custom/`. Copy either pair to try it:

```sh
cp examples/custom/Header.jsx examples/custom/Header.module.css components/
cp examples/custom/Footer.jsx examples/custom/Footer.module.css components/
npx lettercamp dev
```

CSS Modules work through imports such as `import styles from './Header.module.css'`
and `className={styles.header}`. Commit the CSS alongside the component. Local class
names are scoped; inherited typography and global element styles still apply.

The web editor shows placeholders for custom headers and footers from the last
successful build. Edit their files in your repository and use the local preview
or published site to check their appearance. Code and CSS edits, including adding
or removing an override, reload automatically in `lettercamp dev`.

See the [custom headers and footers guide](https://www.lettercamp.com/docs/custom-layout).

## Images and fonts

Use absolute HTTPS URLs for images and fonts. Upload them through the Lettercamp web editor or `lettercamp upload`, or use an existing asset host. Repository `public/` files are not served or copied into previews or builds.

Set `design.typography.headingFont` and `design.typography.bodyFont` independently: use `{ "google": "Lora" }` for a Google font or `{ "url": "https://example.com/brand.woff2", "name": "Brand" }` for a hosted font. Custom font hosts must allow cross-origin requests.

## Layouts

In the web editor, open **Design → Customize**, then **Home → Site** or
**Post → Layout**. Choose **Grid / Rows** for Home and **Horizontal / Vertical** for the post
header. The starter defaults to Grid and Vertical.

The same options work in `settings.json` with both `lettercamp dev` and
`lettercamp build`:

```json
{
  "home": {
    "feedLayout": "grid",
    "showCategories": true,
    "contentWidthPx": 1280
  },
  "post": {
    "heroLayout": "stacked",
    "contentWidthEm": 40,
    "showCover": true,
    "showTableOfContents": true
  }
}
```

Set `home.feedLayout` to `rows` for image-left post rows. Set
`post.heroLayout` to `stacked` for Vertical (text above the image), or `split`
for Horizontal (text beside the image).
`home.contentWidthPx` sets the homepage's maximum content width in pixels
(default: 1280). Adjust it in **Home → Site → Page width (px)**. Grid columns
adapt to the available content width; the setting also applies to Rows.
`post.contentWidthEm` sets the reading width as a multiple of body text size.
The default `40` gives 640px at 16px text and 720px at 18px, capped by the screen
width. Change it in **Post → Content → Reading width** in the design editor.
Vertical uses a left-aligned heading and byline. Its table of contents appears
as small line indicators at the left edge of the screen; hover, focus, or tap to
open the section list. Both layouts adapt to smaller screens. Missing settings use the defaults above; Archive keeps its compact list.

Use **Show categories** in **Home → Site** or set `home.showCategories`
to `false` to hide the category filters above the posts. This works with Grid and
Rows and shows all posts, ignoring category query parameters while hidden. Omit
the setting or set it to `true` to show the filters when categories are available.

Set `design.backgroundColor` in `settings.json` to a six-digit hex color (default `"#ffffff"`). It applies to every page, including the header and footer. In the design editor, **Background color** under **Home → Site** or **Post → Layout** changes this same global setting.
