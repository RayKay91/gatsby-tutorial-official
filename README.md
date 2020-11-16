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


