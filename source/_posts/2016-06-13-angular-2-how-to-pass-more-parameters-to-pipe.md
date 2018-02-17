---
title: Angular 2 - How to pass more parameters to Pipe
id: 841
categories:
  - Angular 2
  - JavaScript
  - TypeScript
  - Angular 2 Pipes
date: 2016-06-13 11:57:40
tags:
  - Angular 2
  - JavaScript
  - TypeScript
  - Angular 2 Pipes
---

Pipes are very important element of Angular 2 framework. With it you can transform and filter your data. But how can you deal with it?
<!--more-->
Lets start with a simple definition of pipe which filters data:
<pre class="line-numbers"><code class="language-javascript">import {Pipe, PipeTransform} from '@angular/core';

@Pipe({
    name: 'filterData',
    pure: false
})

export class FilterData implements PipeTransform {
    transform(items:any[], args:string[]):any[] {
        if (typeof items === 'object') {
            var resultArray = [];
            if (args.length === 0) {
                resultArray = items;
            }

            else {
                for (let item of items) {
                    if (item.name != null &amp;&amp; item.name.match(new RegExp(''+args, 'i'))) {
                        resultArray.push(item);
                    }
                }
            }

            return resultArray;
        }
        else {
            return null;
        }

    }

}</code></pre> 

This pipe will filter your data and as a filtering parameter will get an param passed as a args:string[]. So easily when you want to add text input which will be a filtering string you need to connect it with your pipe in component like this:

<pre class="line-numbers"><code class="language-javascript">&lt;input type="text" #filter (keyup)="0"&gt;</code></pre> 

Now when you want to filter your data by string passed into input you need to get a value of #filter element like this (filter.data): 

<pre class="line-numbers"><code class="language-javascript">&lt;div class="row" *ngFor="let point of (points | filterData: filter.value"&gt;</code></pre> 

## Pass a string as a parameter

To pass more parameters to your Pipe you will need to change a little your Pipe definition:

<pre class="line-numbers"><code class="language-javascript">export class FilterData implements PipeTransform {
    transform(items:any[], args:string[], additionl):any[] {
        console.log(additionl);</code></pre> 

So as you can see you are just passing new parameter to your Pipe. Now when you want to pass it from  your template you need to add it like it is in example:

<pre class="line-numbers"><code class="language-javascript">&lt;div class="row" *ngFor="let point of (points | filterData: filter.value : 'name')"&gt;</code></pre> 

After it you will see that passed parameter 'name' will be displayed  in your console.

## Pass array as a parameter

But what if you want to pass an array of elements? It is possible too! You can do this like this without changing your Pipe definition.

<pre class="line-numbers"><code class="language-javascript">&lt;div class="row" *ngFor="let point of (points | filterData: filter.value : ['all','name'])"&gt;
</code></pre> 

## Pass object as a parameter

Yes you can pass an object as a parameter to your pipe. You cannot be limited in case you want to pass more than one parameter - you can pass an object of parameters too. To do that you can just do it from template of your component as it is described in code example:

<pre class="line-numbers"><code class="language-javascript">&lt;div class="row" *ngFor="let point of (points | filterData: filter.value : {name: true})"&gt;</code></pre> 

So this can be a base to extend your pipes! You dont need to base it on one passed element!
