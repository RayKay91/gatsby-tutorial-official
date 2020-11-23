<!-- AUTO-GENERATED-CONTENT:START (STARTER) -->
<p align="center">
  <a href="https://www.gatsbyjs.com">
    <img alt="Gatsby" src="https://www.gatsbyjs.com/Gatsby-Monogram.svg" width="60" />
  </a>
</p>
<h1 align="center">
  Gatsby's hello-world starter
</h1>

#### Starting a project

---

To start a new project run in Terminal:

```shell
gatsby new PROJECTNAME STARTER-SITE-LINK
```

If starter site repo isn't linked it'll set up gatsby using the default starter.

To run the development server you do

```shell
gatsby develop
```

It'll go live with hot reloading enabled on `http://localhost:8000/`.

**Linking between pages**

Import Link:

```
import { Link } from 'gatsby'
```

Use the component and give it a 'to' prop of the path that you want:

```
export default function Link(){
  return (
      <Link to='/contact/'>Contact us</Link>
  )
}
```

_Remember:_ make the the filename for the page the same as the path you entered as a prop to `<Link to = />` otherwise it won't find the page.

For external links you still use the `<a></a>` tag.

**Building and deploying**
You can build using `gatsby build` and then use the public folder to upload to the server like netlify or surge.

### Styling and CSS in Gatsby

**Global styling**

Create a folder in `src` named `styles` and in there create a file called `global.css`. In this file put some global css rules you want to apply sitewide.

Create a new file called `gatsby-browser.js` in the root and in there import the global styles.

`import "./src/styles/global.css"`

**Component scoped styling**

You could use CSS modules which works out of the box with Gatsby.

Import the CSS module file named `samenameascomponent.module.css` into the component:

```
import React from 'react'
import styles from './path/to/name.module.css'

export default function randomComponent() {
  return (
    <div className={ styles.NAMEOFCLASSINCSSMODULESFILE }>Lorem ipsum</div>
  )
}
```

This is the CSS Modules method.

Note: for the `<Link />` tag you can use activeClassName as a prop and then use the CSS Modules method to choose a class that will be applied when that link is the active link (i.e. displayed in the browser).

**Or** you can use something like StyledComponents or Emotion to have locally scoped styles. Tutorials can be found on the gatsby site.

### Plugins

[You can checkout the plugin library for Gatsby here.](https://www.gatsbyjs.com/plugins/)

You configure the plugins and tell Gatsby to use them and any options for them in the `gatsby-config.js` file.

The plugins will have instuctions on how to use them.

Changes made to the `gatsby-config.js` file will require a restart of the dev server for changes to be put into effect.

### Data in Gatsby

Data in Gatsby is everything that's not a React component. You can use things like GraphQL to query APIs to pull in data from other services to populate the site.

You can use Gatsby's `createPages` API to use a different method of pulling in data, but by doing so you lose a lot of benefits that come with Gatsby. Check the API page for more details.

Instead use the _Gatsby way of doing things_ which is to use **Graph QL**.

You can query things like site metadata and bits of data that you want to share across components without having to update them individually each time you change them.

To set the site metadata in `gatsby-config.js`:

```
module.exports = {
siteMetadata: {
  title: `Title from siteMetadata`,
},
plugins: [...],
}
```

Then, to query this from the page:

1. `import { graphql } from 'gatsby`
1. Pass in `{ data } into the functional component`
1. Access the data you want using dot notation: `{ data.site.siteMetadata.title }`
1. Export the query from the page file:

```
import React from "react"
import { graphql } from "gatsby"
import Layout from "../components/layout"

export default function About({ data }) {
  return (
    <Layout>
      <h1>About {data.site.siteMetadata.title}</h1>
      <p>
        We're the only site running on your computer dedicated to showing the
        best photos and videos of pandas eating lots of food.
      </p>
    </Layout>
  )
}

export const query = graphql`
  query {
    site {
      siteMetadata {
        title
      }
    }
  }
`
```

<u>Note</u>: Page queries live outside of the component definition — by convention at the end of a page component file — and are only available on page components.

**Static Queries**

These are a new API introduced in Gatsby 2 and it allows non-page components (like layout.js for example) to retrieve data via GraphQL queries.

Example in layout.js (_a component not a page_)

```
import React from "react"
import { css } from "@emotion/core"
import { useStaticQuery, Link, graphql } from "gatsby"

import { rhythm } from "../utils/typography"
export default function Layout({ children }) {
  const data = useStaticQuery(
    graphql`
      query {
        site {
          siteMetadata {
            title
          }
        }
      }
    `
  )
  return (
    <div
      css={css`
        margin: 0 auto;
        max-width: 700px;
        padding: ${rhythm(2)};
        padding-top: ${rhythm(1.5)};
      `}
    >
      <Link to={`/`}>
        <h3
          css={css`
            margin-bottom: ${rhythm(2)};
            display: inline-block;
            font-style: normal;
          `}
        >
          {data.site.siteMetadata.title}
        </h3>
      </Link>
      <Link
        to={`/about/`}
        css={css`
          float: right;
        `}
      >
        About
      </Link>
      {children}
    </div>
  )
}
```

In short - use page queries if querying from a page, and use `useStaticQuery` if querying from a component.
