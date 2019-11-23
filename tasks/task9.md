# Task 9 - Add the number of items to the cart

**Learnings**

- Adding styled-components
- using the [reduce() function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)
- Adding the `useContext` and `ShopContext`

**Task Definition**

Add the total items count to the "Cart" navigation link in the navigation bar 

**Files**

- `src/components/Navigation.js`


**Example**

To use styled componets import the `styled` library, Then add some style 

```jsx
  import styled from 'styled-components'

  const ListItem = styled.li`
    position: relative;
  `

  const Count = styled.span`
    position: absolute;
    top: -6px;
    margin-left: 4px;
    font-weight: 400;
    font-size: 14px;
  `
```

To get information about the cart totals etc import the `{useContext}` react function and import the `../context` functions and use the `ShopContext` function from that file.

```jsx
import React, { useContext } from 'react'
import {ShopContext} from '../context'
```

Then use the `checkout` from `useContext(ShopContext)`

```jsx

function Navigation() {
  const { checkout } = useContext(ShopContext)

  const cartCount = checkout
    ? checkout.lineItems.reduce((accumulator, lineItem) => accumulator + lineItem.quantity, 0)
    : 0
```

**Result**

<details>
  <summary>Click here to see the end result</summary>
  <p>

```jsx
// Navigation.js
import React, { useContext } from 'react'
import { Link } from "react-router-dom"
import logo from '../images/logo_black.png'
import {ShopContext} from '../context'
import React, { useContext } from 'react'
import styled from 'styled-components'

const ListItem = styled.li`
  position: relative;
`

const Count = styled.span`
  position: absolute;
  top: -6px;
  margin-left: 4px;
  font-weight: 400;
  font-size: 14px;
`

function Navigation() {

  const { checkout } = useContext(ShopContext)

  const cartCount = checkout
    ? checkout.lineItems.reduce((accumulator, lineItem) => accumulator + lineItem.quantity, 0)
    : 0

  return (
    <nav>
      <ul>
        <ListItem>
          <Link to="/">
            <img src={logo} alt="Home" />
          </Link>
        </ListItem>
        <ListItem>
          <Link to="/why-us">Why Us</Link>
        </ListItem>
        <ListItem>
          <Link to="/our-services">Our Services</Link>
        </ListItem>
        <ListItem>
          <Link to="/cart">Cart <Count>{cartCount}</Count></Link>
        </ListItem>
      </ul>
    </nav>
  )
}

export default Navigation
```

  </p>
</details>

**[← Previous task](./task8.md)** | **[Next task →](./task8.md)**