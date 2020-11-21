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

   To start a new project run  in Terminal:
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
*Remember:* make the the filename for the page the same as the path you entered as a prop to `<Link to = />` otherwise it won't find the page.

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

**Or** you can use something like StyledComponents or Emotion to have locally scoped styles. Tutorials can be found on the gatsby site.

### Nested Layout Components