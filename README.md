# declarative-router
A declarative router that uses React Navigation under the hood. JSX, compound components, render props

This is an exploration in designing a declarative router. It might become a real thing, or it might just remain a thought experiment.

Let me know what you think.

Initial API
https://gist.github.com/wolverineks/b4c074092f39fc9492a9e395414cc96f

Development Preferences
* Prefer changes that decrease responsibilities to changes that increase responsibilities
* Prefer changes that reduce API surface area to changes that increase API surface area
* Prefer changes that increase flexibility to changes that decrease flexibility

Feature Description
* `<Router>` / `<Scenes>` / `<Headers>` / `<Bodies>` / `<Tabs>` know how to apply styles to `this.props.children` such that they transition in / out of the "view window"

```javascript
import { Bodies, Body, Drawers, Drawer, Headers, Header, Router, Route, Tabs, Tab } from 'declarative-router'
import { Scene1, Scene2 } from './myScenes'
import { Main } from './myRoutes'

<Router>{(route) =>
  // Routes ////////////////////////////////////////////////////////////////
  <Route isActive={route === 'main'}>{(scene) =>
    <Scene isActive={scene === '1'}>
      // DRAWERS ////////////////////////////////////////////////////////////////
      <Drawers>
        <Drawer isActive={scene === '1'}>
          <Scene1.Drawer />
        </Drawer>

        <Drawer isActive={scene === '2'}>
          <Scene2.Drawer />
        </Drawer>
      </Drawers>

      // HEADERS ////////////////////////////////////////////////////////////////
      <Headers>
        <Header isActive={scene === '1'}>
          <Scene1.Header>
            <Scene1.Header.Left onPress={headersScene1LeftPressed} />
            <Scene1.Header.Center onPress={headersScene1CenterPressed} />
            <Scene1.Header.Right onPress={headersScene1RightPressed} />
          </Scene1.Header>
        </Header>

        <Header isActive={scene === '2'}>
          <Scene2.Header>
            <Scene2.Header.Left onPress={headersScene2LeftPressed} />
            <Scene2.Header.Center onPress={headersScene2CenterPressed} />
            <Scene2.Header.Right onPress={headersScene2RightPressed} />
          </Scene2.Header>
        </Header>
      </Headers>

      // BODIES ////////////////////////////////////////////////////////////////
      <Bodies>
        <Body isActive={scene === '1'}>
          <Scene1.Body onPress={headersScene1Pressed} />
        </Body>

        <Body isActive={scene === '2'}>
          <Scene2.Body onPress={headersScene2Pressed} />
        </Body>
      </Bodies>

      // TABS ////////////////////////////////////////////////////////////////
      <Tabs>
        <Tab isActive={scene === '1'}>
          <Scene1.Tab onPress={scene1TabButtonPressed} />
        </Tab>

        <Tab isActive={scene === '2'}>
          <Scene2.Tab onPress={scene2TabButtonPressed} />
        </Tab>
      </Tabs>
    </Main>
  }</Route>
}</Router>
```
