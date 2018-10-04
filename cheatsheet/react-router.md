# React-Router Cheatsheets

**install dependency**
```javascript
$ npm install --save react-router-dom
```

**Routes**
```javascript
import { 
  BrowserRouter, 
  Route 
} from 'react-router-dom'

const Hello = () => <h1>Hello world!</h1>

const App = () => (
  <BrowserRouter>
    <div>
      <Route path="/hello" component={Hello}/>
    </div>
  </BrowserRouter>
)

// open: http://localhost:3000/hello
```

**Switch**

Renders the first `<Route>` that matches the location.
```javascript
import  { 
  BrowserRouter, 
  Switch, 
  Route 
} from 'react-router'

const YourComponent = () => (
  <BrowserRouter>
    <Switch>
      <Route exact path="/" component={Home}/>
      <Route path="/about" component={About}/>
      <Route path="/:user" component={User}/>
      <Route component={NoMatch}/>
    </Switch>
  </BrowserRouter>
);

export default YourComponent
```

**Link**
```javascript
import { Link } from 'react-router-dom'

const Links = ({ match }) => (
  <nav>
    <Link to="/">Home</Link>
    <Link to={{ pathname: '/dashboard' }}>
      Dashboard
    </Link>
    <Link replace to="/about">About</Link>
  </nav>
)

export default Links
```

**NavLink**
```javascript
import { NavLink } from 'react-router-dom'

const Links = ({ match }) => (
  <nav>
    <NavLink activeClassName="active" to="/">
      Home
    </NavLink>
    <NavLink activeClassName="active" to="/dashboard">
      Dashboard
    </NavLink>
    <NavLink activeClassName="active" to="/about">
      About
    </NavLink>
  </nav>
)

export default Links
```

**match**
```javascript
const Dashboard = ({ match }) => (
  <ul>
    <li>params: {JSON.stringify(match.params)}</li>
    <li>isExact: {match.isExact.toString()}</li>
    <li>path: {match.path}</li>
    <li>url: {match.url}</li>
  </ul>
)

<Route path="/dashboard" component={Dashboard}/>
```
