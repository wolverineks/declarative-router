# declarative-router
A declarative router that uses React Navigation under the hood. JSX, compound components, render props

Initial API
https://gist.github.com/wolverineks/b4c074092f39fc9492a9e395414cc96f

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
