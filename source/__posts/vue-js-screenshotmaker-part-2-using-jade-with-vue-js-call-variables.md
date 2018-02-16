---
title: 'Vue.js - ScreenshotMaker part 2 (using Jade with Vue.js, call variables)'
id: 978
categories:
  - Front End
  - Vue.js
date: 2016-08-16 11:00:38
tags:
---

Each project needs evolution. After a comment by Peter van Meijgaard (https://github.com/petervmeijgaard) in previous post (http://fedojo.com/vue-js-first-look-and-test/) Ive made a few changes.

<!--more-->

## Changes in variables

Previously:

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
    }`</pre>
    Current:
    <pre class="line-numbers">`methods: {
                makeScreenshot: function(e) {
                    this.form = false;
                    this.inprogress = true;

                    Vue.http.get('http://localhost:8888/screenshot?url='+this.url).then((response) =&gt; {
                        var res = JSON.parse(response.body);
                        this.success = true;
                        this.inprogress = false;
                    }, (response) =&gt; {
                        this.error = true;
                        this.inprogress = false;
                    });
                }
            }`</pre>
    So the changes are visible in each call to variables defined in data function:
    <pre class="line-numbers">`data(){
                return {
                    form: true,
                    error: false,
                    success: false,
                    inprogress: false,
                    url: ''
                }
    },`</pre>
    It doesnt need usage:
    <pre class="line-numbers">`this.$set('success', true);`</pre>
    It can be done with:
    <pre class="line-numbers">`this.success = true;

## Usage of JADE instead raw HTML

I love preprocessors and wished to use JADE templating. It is possible in Vue.js to define template in .vue file as a JADE. To do that you need to add JADE to your node_modules:
<pre class="lang:default decode:true ">sudo npm i jade --save</pre>
Now you can bring your JADE code in template section:
<pre class="line-numbers">`&lt;template&gt;
    p This is screenshotmaker!
    div(v-if="form")
        input(v-model="url", placeholder="URL")
        button(v-on:click="makeScreenshot") Make screenshot
    div(v-if="error")
        p Error
    div(v-if="success")
        p Screenshot done!
    div(v-if="inprogress")
        p In progress
&lt;/template&gt;

&lt;style&gt;

&lt;/style&gt;

&lt;script lang="babel"&gt;
    import Vue from 'vue';

    export default{
        data(){
            return {
                form: true,
                error: false,
                success: false,
                inprogress: false,
                url: ''
            }
        },
        methods: {
            makeScreenshot: function (e) {
                this.form = false;
                this.inprogress = true;

                Vue.http.get('http://localhost:8888/screenshot?url=' + this.url).then((response) =&gt; {
                    var res = JSON.parse(response.body);
                    this.success = true;
                    this.inprogress = false;
                }, (response) =&gt; {
                    this.error = true;
                    this.inprogress = false;
                });
            }
        }
    }
&lt;/script&gt;`
</pre>

Changes are visible in [https://github.com/fedojo/screenshot-maker-fe-vue/tree/v0.2-jade](https://github.com/fedojo/screenshot-maker-fe-vue/tree/v0.2-jade)