---
title: ScreenshotMaker with Vue.js - First look at Vue.js (HTTP and simple component)
id: 939
categories:
  - Front End
  - Vue.js
  - ScreenshotMaker
  - JavaScript
  - HTTP
  - AJAX
date: 2016-08-12 15:34:05
tags:
---

Currently everybody is focused on most trendy JS frameworks like Angular 2 and React. This giants are taking the most of Front End market. Ive heard a little bit about Vue.js but I gave it a small chance.
<!--more-->

## Vue.js CLI

Vue.js comes with CLI so it is easier to deal with it.
The official website of CLI project: [https://github.com/vuejs/vue-cli](https://github.com/vuejs/vue-cli).

To install it on MAC you will need to run the command:
<pre class="line-numbers"><code class="language-javascript">sudo npm install -g vue-cli</code></pre>

To create a project Ive used webpack template:

<pre class="line-numbers"><code class="language-javascript">vue init webpack my-project</code></pre>

It create for me a simple structure and the next instructions were listed:

<pre class="line-numbers"><code class="language-javascript">npm install
npm run dev </code></pre>


After that Ive could run browser with URL http://localhost:8080/ and see the first view.

[![Screen Shot 2016-08-10 at 16.01.21](http://fedojo.com/wp-content/uploads/2016/08/Screen-Shot-2016-08-10-at-16.01.21.png)](http://fedojo.com/wp-content/uploads/2016/08/Screen-Shot-2016-08-10-at-16.01.21.png)

&nbsp;

## Install Vue.js dev tools

For easier and better work with Vue.js it is recommended to use Vue dev tools.
Official repository of Vue.js dev tools: [https://github.com/vuejs/vue-devtools](https://github.com/vuejs/vue-devtools)
To download it use this link: [https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
[![Vue.js - dev tools](http://fedojo.com/wp-content/uploads/2016/08/Screen-Shot-2016-08-10-at-16.15.21.png)](http://fedojo.com/wp-content/uploads/2016/08/Screen-Shot-2016-08-10-at-16.15.21.png)

## PHPStorm/WEBStorm and Vue.js

To deal with .vue files it will be good to install a plugin [https://plugins.jetbrains.com/plugin/8057?pr=phpStorm](https://plugins.jetbrains.com/plugin/8057?pr=phpStorm)

&nbsp;

## Connect with an API

My API test is working on Node and serves 2 options:
- list screenshots.
- make a screenshots

both are GET methods.

Lets start with getting list from server.

## Component which invokes GET on server

Ive used a structure which is done by VUE CLI and added functionality to component which was created by it. To start working with HTTP requests you need to install a package VueResource.
<pre class="line-numbers"><code class="language-javascript">sudo npm i vue-resource --save</code></pre>
Than edit main.js:
<pre class="line-numbers"><code class="language-javascript">import Vue from 'vue';
import VueResource from 'vue-resource';
import App from './App';

Vue.use(VueResource);
Vue.http.options.emulateJSON = true;

var vueApp = new Vue({
    el: 'body',
    components: {App},
})</code>
</pre>

Additionally the App.vue file which describes App component looks like this:

<pre class="line-numbers"><code class="language-javascript">&lt;template&gt;
  &lt;div id="app"&gt;
    &lt;img class="logo" src="./assets/logo.png"&gt;
    &lt;ul&gt;
      &lt;li v-for="(index, item) in items"&gt;
        {{ item }}
      &lt;/li&gt;
    &lt;/ul&gt;
  &lt;/div&gt;

&lt;/template&gt;

&lt;script&gt;
import Vue from 'vue';

export default {
  data: function(){
    return { items: [ 'ding']};
  },
  ready: function() {
    this.fetchFiles();
  },

  methods: {
    fetchFiles: function() {
      Vue.http.get('http://localhost:8888/list').then((response) =&gt; {
        var res = JSON.parse(response.body);
        this.$set('items', res.files);

      }, (response) =&gt; {
        console.log(response);
      });
    }
  }
}
&lt;/script&gt;

&lt;style&gt;
html {
  height: 100%;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

#app {
  color: #2c3e50;
  margin-top: -100px;
  max-width: 600px;
  font-family: Source Sans Pro, Helvetica, sans-serif;
  text-align: center;
}

#app a {
  color: #42b983;
  text-decoration: none;
}

.logo {
  width: 100px;
  height: 100px
}
&lt;/style&gt;
</code></pre>

The most important for us fragments of code are:

### Directive which will render our list:
<pre class="line-numbers"><code class="language-javascript">&lt;li v-for="(index, item) in items"&gt;
     {{ item }}
&lt;/li&gt;</code></pre>

### Method which fetches data from server:

<pre class="line-numbers"><code class="language-javascript">fetchFiles: function() {
      Vue.http.get('http://localhost:8888/list').then((response) =&gt; {
        var res = JSON.parse(response.body);
        this.$set('items', res.files);

      }, (response) =&gt; {
        console.log(response);
      });
    }</code></pre>

### This line:
<pre class="line-numbers"><code class="language-javascript">this.$set('items', res.files);</code></pre>

### Changes the data which needs to be rendered in directive. Data is described as a function which returns object:
<pre class="line-numbers"><code class="language-javascript">data: function(){
    return { items: [ 'ding']};
  },</code></pre>
Effect after HTTP request:

![Vue.js - list after request](http://fedojo.com/wp-content/uploads/2016/08/Screen-Shot-2016-08-12-at-12.38.56.png)

&nbsp;

Without our HTTP request done by fetchFiles method the list will be rendering only one item "ding".

[![Vue.js - list without request](http://fedojo.com/wp-content/uploads/2016/08/Screen-Shot-2016-08-12-at-12.38.45.png)](http://fedojo.com/wp-content/uploads/2016/08/Screen-Shot-2016-08-12-at-12.38.45.png)

This version of code is available here:
[https://github.com/fedojo/screenshot-maker-fe-vue/commit/1c5fabacc3ed362abe995cf7da3ddfa8f7d1defa](https://github.com/fedojo/screenshot-maker-fe-vue/commit/1c5fabacc3ed362abe995cf7da3ddfa8f7d1defa)

## Router

To start working with router you will need to install new package available under link[ https://github.com/vuejs/vue-router](https://github.com/vuejs/vue-router).
Official documentation is available here: [http://router.vuejs.org/](http://router.vuejs.org/)

Lets install the package:
<pre class="line-numbers"><code class="language-javascript">npm install vue-router</code></pre>

## Router in depth

To start working with router we need to change a little bit our structure. Our aproach is to create an app with two links:
- list - with list of screenshots
- makescreenshot - with simple form which creates a screenshot

Firstly we need to create components for both views.

Structure:
|- componenents
||- List.vue
||- MakeScreenshot.vue
|- main.js

File main.js:

<pre class="line-numbers"><code class="language-javascript">import Vue from 'vue';
import VueResource from 'vue-resource';
import VueRouter from 'vue-router';

// Components
import List from './components/List';
import MakeScreenshot from './components/MakeScreenshot';

// HTTP configuration
Vue.use(VueResource);
Vue.http.options.emulateJSON = true;

var App = Vue.extend({
    template: `
        &lt;div id="app"&gt;
          &lt;h1&gt;Screenshot App!&lt;/h1&gt;
          &lt;p&gt;
            &lt;a v-link="{ path: '/list' }"&gt;Go to List&lt;/a&gt;
            &lt;a v-link="{ path: '/makescreenshot' }"&gt;Make screenshot&lt;/a&gt;
          &lt;/p&gt;
          &lt;!-- route outlet --&gt;
          &lt;router-view&gt;&lt;/router-view&gt;
        &lt;/div&gt;
    `
});

// Router configuration
Vue.use(VueRouter);
var router = new VueRouter();

router.map({
    '/list': {
        component: List
    },
    '/makescreenshot': {
        component: MakeScreenshot
    }
});

// Start app
router.start(App, 'app');</code></pre>

List.vue

<pre class="line-numbers"><code class="language-javascript">&lt;template&gt;
    &lt;p&gt;This is list!&lt;/p&gt;
    &lt;ul&gt;
        &lt;li v-for="(index, item) in items"&gt;
            {{ item }}
        &lt;/li&gt;
    &lt;/ul&gt;
&lt;/template&gt;
&lt;style&gt;

&lt;/style&gt;
&lt;script&gt;
    import Vue from 'vue';

    export default{
        data: function(){
            return { items: [ 'ding']};
        },
        ready: function() {
            this.fetchFiles();
        },

        methods: {
            fetchFiles: function() {
                Vue.http.get('http://localhost:8888/list').then((response) =&gt; {
                    var res = JSON.parse(response.body);
                this.$set('items', res.files);

            }, (response) =&gt; {
                    console.log(response);
                });
            }
        }
    }
&lt;/script&gt;
</code></pre>

Make screenshot:

<pre class="line-numbers"><code class="language-javascript">&lt;template&gt;
    &lt;p&gt;This is screenshotmaker!&lt;/p&gt;
    &lt;div v-if="form"&gt;
        &lt;input v-model="url" placeholder="URL" /&gt;
        &lt;button v-on:click="makeScreenshot"&gt;Make screenshot&lt;/button&gt;
    &lt;/div&gt;
    &lt;div v-if="error"&gt;
        &lt;p&gt;Error&lt;/p&gt;
    &lt;/div&gt;
    &lt;div v-if="success"&gt;
        &lt;p&gt;Screenshot done!&lt;/p&gt;
    &lt;/div&gt;
    &lt;div v-if="inprogresss"&gt;
        &lt;p&gt;In progress&lt;/p&gt;
    &lt;/div&gt;
&lt;/template&gt;

&lt;style&gt;
&lt;/style&gt;

&lt;script&gt;
    import Vue from 'vue';

    export default{
        data(){
            return {
                form: true,
                error: false,
                success: false,
                inprogresss: false,
                url: ''
            }
        },
        methods: {
            makeScreenshot: function(e) {
                this.$set('form', false);
                this.$set('inprogresss', true);

                Vue.http.get('http://localhost:8888/screenshot?url='+this.url).then((response) =&gt; {
                    var res = JSON.parse(response.body);
                    this.$set('success', true);
                    this.$set('inprogresss', false);
                }, (response) =&gt; {
                    this.$set('error', true);
                    this.$set('inprogresss', false);
                });
            }
        }
    }
&lt;/script&gt;
</code></pre>

After creating this app you can see this view in browser:

[![Vue.js - routing](http://fedojo.com/wp-content/uploads/2016/08/ScreenshotApp_routing.gif)](http://fedojo.com/wp-content/uploads/2016/08/ScreenshotApp_routing.gif)

As you can see after clicking on links you are moved to selected components. Main router configuration is done in this lines:

<pre class="line-numbers"><code class="language-javascript">router.map({
    '/list': {
        component: List
    },
    '/makescreenshot': {
        component: MakeScreenshot
    }
});</code></pre>

Here you can see the configuration of routes in project and selected component. To make a router alive you need to add links in your component and additionally router-outlet which can be added with router-view tag.

<pre class="line-numbers"><code class="language-javascript">var App = Vue.extend({
    template: `
        &lt;div id="app"&gt;
          &lt;h1&gt;Screenshot App!&lt;/h1&gt;
          &lt;p&gt;
            &lt;a v-link="{ path: '/list' }"&gt;Go to List&lt;/a&gt;
            &lt;a v-link="{ path: '/makescreenshot' }"&gt;Make screenshot&lt;/a&gt;
          &lt;/p&gt;
          &lt;!-- route outlet --&gt;
          &lt;router-view&gt;&lt;/router-view&gt;
        &lt;/div&gt;
    `
});</code></pre>

## Making screenshots and If directive in Vue.js

Vue.js has implemented if directive which can make your life easier when you want to add conditional displaying of elements in your component.

In MakeScreenshot.vue you can see v-if attribute in elements.

<pre class="line-numbers"><code class="language-javascript">&lt;template&gt;
    &lt;p&gt;This is screenshotmaker!&lt;/p&gt;
    &lt;div v-if="form"&gt;
        &lt;input v-model="url" placeholder="URL" /&gt;
        &lt;button v-on:click="makeScreenshot"&gt;Make screenshot&lt;/button&gt;
    &lt;/div&gt;
    &lt;div v-if="error"&gt;
        &lt;p&gt;Error&lt;/p&gt;
    &lt;/div&gt;
    &lt;div v-if="success"&gt;
        &lt;p&gt;Screenshot done!&lt;/p&gt;
    &lt;/div&gt;
    &lt;div v-if="inprogresss"&gt;
        &lt;p&gt;In progress&lt;/p&gt;
    &lt;/div&gt;
&lt;/template&gt;</code></pre>

As a value in v-if attribute are used variables defined in component data function:

<pre class="line-numbers"><code class="language-javascript">data(){
            return {
                form: true,
                error: false,
                success: false,
                inprogresss: false,
                url: ''
            }
        },</code></pre>

This values are changed in makeScreenshot function. When button is clicked form is hidden and inprogress fragment is displayed. When request is done with success inprogress fragment is hidden and success is showed. When we have error in request the error is viewed and inprogress hidden.

<pre class="line-numbers"><code class="language-javascript">makeScreenshot: function(e) {
                this.$set('form', false);
                this.$set('inprogresss', true);

                Vue.http.get('http://localhost:8888/screenshot?url='+this.url).then((response) =&gt; {
                    var res = JSON.parse(response.body);
                    this.$set('success', true);
                    this.$set('inprogresss', false);
                }, (response) =&gt; {
                    this.$set('error', true);
                    this.$set('inprogresss', false);
                });
}</code></pre>

The effect in browser:

[![Vue.js - if directive](http://fedojo.com/wp-content/uploads/2016/08/ScreenshotApp_if.gif)](http://fedojo.com/wp-content/uploads/2016/08/ScreenshotApp_if.gif)

## Summary

The basics of Vue.js are simple to get. The routing and HTTP request could be included in the core package. But maybe it is better to keep it out of core and make a lib smaller. After this short project I think that Vue.js is very good and small framework and easy to learn. Looks at some points it's pretty similar to Angular 1.

You can check the sources of project here:
[https://github.com/fedojo/screenshot-maker-fe-vue](https://github.com/fedojo/screenshot-maker-fe-vue)
