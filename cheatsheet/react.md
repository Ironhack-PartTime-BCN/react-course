# React Cheatsheets

## Create-react-app
```bash
$ create-react-app YOUR_APP_NAME
```

## React

**Stateless Component**
```javascript
import React from 'react'

const YourComponent = (props) => <div>{props.name}</div>

export default YourComponent
```

**Class Component**
```javascript
import React from 'react'

class YourComponent extends React.Component {
  render() {
    return <div>aaa</div>
  }
}

export default YourComponent
```

**State**
```javascript
class CountClicks extends React.Component {
  state = {
    clicks: 0
  }

  onButtonClick = () => {
    this.setState(prevState => ({
      clicks: prevState.clicks + 1
    }))
  }

  render() {
    return (
      <div>
        <button onClick={this.onButtonClick}>
          Click me
        </button>
        <span>
          The button clicked 
          {this.state.clicks} times.
        </span>
      </div>
    )
  }
}
```

**Ref**
```javascript
class AutoFocusTextInput extends React.Component {
  constructor(props) {
    super(props);
    this.textInput = React.createRef();
  }

  componentDidMount() {
    this.textInput.current.focus();
  }

  render() {
    return (
      <input ref={this.textInput} />
    );
  }
}
```

**Higher Order Component**
```javascript
import React from 'react'
import Loading from '../components/Loading'

const withLoading = WrappedComponent => {
  return (props = {}) => {
    if (props.isLoading) {
      return <Loading />
    }
    return <WrappedComponent {...this.props} />
  }
}

export default withLoading

// --------

const MyComponent = ({}) => <div /> // ...
const WithLoadingComponent = withLoading(MyComponent)
```

**Render Props**
```javascript
import React from 'react'

const MOBILE_VIEW_WIDTH_THRESHOLD = 600

class MediaQuery {
  state = {
    shouldShowMobileView: false
  }

  componentDidMount() {
    addEventListener('resize', this.updateResizeStatus)
  }

  componentWillUnmount() {
    removeEventListener('resize', this.updateResizeStatus)
  }

  updateResizeStatus() {
    if (screen.width <= MOBILE_VIEW_WIDTH_THRESHOLD) {
      this.setState({
        shouldShowMobileView: true
      })
    }
  }

  render() {
    return this.props.children(
      this.state.shouldShowMobileView
    )
  }
}

export default MediaQuery

// --------

import React from 'react'
import MobileView from '../components/MobileView'
import DefaultView from '../components/DefaultView'

const Screen = () => (
  <MediaQuery>
    {shouldShowMobileView =>
      shouldShowMobileView ? (
        <MobileView />
      ) : (
        <DefaultView />
      )
    }
  </MediaQuery>
)
```