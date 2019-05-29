---
layout: post
title:  "Typescript 配置路由"
date:   2018-08-13 22:39:00 +0800
tags: typescript react react-redux react-router redux-saga webpack tslint
---


{% highlight js %}
cnpm i -S react-router-dom @types/react-router-dom
{% endhighlight %}

index.tsx
{% highlight js %}
import * as React from 'react';
import { render } from 'react-dom';
import { HashRouter } from 'react-router-dom';

import App from './containers/App';

render(
  <HashRouter>
    <App/>
  </HashRouter>,
  document.getElementById('root'),
);

{% endhighlight %}

App.tsx
{% highlight js %}
import * as React from 'react';
import { Switch, Link, Route } from 'react-router-dom';

const Home = () => <h1>home</h1>;
const Books = () => <h1>book list</h1>;

export default class App extends React.Component {
  public render() {
    return (
      <div>
        <header>header</header>
        <Link to="/" >home</Link>
        <Link to="/books" >books</Link>
        <main>
          <Switch>
            <Route path="/" component={Home} exact={true} />
            <Route path="/books" component={Books} />
          </Switch>
        </main>
      </div>
    );
  }
}

{% endhighlight %}
