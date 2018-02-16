---
title: Angular 2 RC1 - Pipes and Http
id: 805
categories:
  - Angular
  - Angular 2
  - JavaScript
  - TypeScript
date: 2016-06-02 10:04:32
tags:
---

Ive been trying to build simple filtering in application -> Show-ur-bugs ([https://github.com/fedojo/show-ur-bugs](https://github.com/fedojo/show-ur-bugs)).
 <!--more-->

Let me introduce the error environment firstly:
&nbsp;
project-list.component.ts
<pre class="lang:default decode:true " >import 'rxjs/add/operator/map';
import {Component, OnInit} from '@angular/core';
import {ProjectService} from "../../shared";
import {ProjectListSingleComponent} from "./project/project-list-single.component";
import {FilterData} from "../../filter-data.pipe";

@Component({
    moduleId: module.id,
    bindings: [ProjectService],
    selector: 'app-project-list',
    templateUrl: 'project-list.component.html',
    styleUrls: ['project-list.component.css'],
    directives: [ProjectListSingleComponent],
    pipes: [FilterData]

})

export class ProjectListComponent implements OnInit {
    projects;

    constructor(public projectService:ProjectService) {

    }

    getProjects() {
        this.projectService.getProjects()
            .subscribe(
                data =&gt; {
                    this.projects = data;
                },
                error =&gt; console.error('Error: ' + error[0]),
                () =&gt; {}
            )
    }

    ngOnInit() {
        this.getProjects();
    }

}</pre>

project-list.component.html
<pre class="lang:default decode:true ">&lt;input type="text" #filter (keyup)="0"&gt;

&lt;project-list-single *ngFor="let project of (projects | filterData: filter.value)"
                         [project]="project"
                         class="project"&gt;&lt;/project-list-single&gt;</pre>

filter-data.pipe.ts - ver 1
<pre class="lang:default decode:true " >import {Pipe, PipeTransform} from '@angular/core';
import {ProjectItem} from './projects/index';

@Pipe({
    name: 'filterData'
})
export class FilterData implements PipeTransform {

    transform(value:ProjectItem[], args:string[]):any {
        if (value.length === 0) {
           return value;
        }

        var resultArray = [];

        for (let item of value) {
            if (item.name.match('^.*' + args[0] + '.*$')) {
                 resultArray.push(item);
            }
        }

        return resultArray;
    }

}
</pre>

And the error occured in console:
[![Screen Shot 2016-06-02 at 11.18.19](http://fedojo.com/wp-content/uploads/2016/06/Screen-Shot-2016-06-02-at-11.18.19.png)](http://fedojo.com/wp-content/uploads/2016/06/Screen-Shot-2016-06-02-at-11.18.19.png)

The most important for me was:

> ORIGINAL EXCEPTION: TypeError: Cannot read property 'length' of undefined

But which element hasnt got length? After quick investigation in code it was object which was passed to the Pipe. It havent exist in moment when the Pipe was invoked. So here came an idea to resolve it:

filter-data.pipe.ts - ver 2
<pre class="lang:default decode:true " >import {Pipe, PipeTransform} from '@angular/core';
import {ProjectItem} from './projects/index';

@Pipe({
    name: 'filterData'
})
export class FilterData implements PipeTransform {

    transform(value:ProjectItem[], args:string[]):any {

        if (typeof value === 'object') {
            var resultArray = [];

            if (args.length === 0) {
                for (let item of value) {
                    resultArray.push(item);
                }
            }

            else {
                for (let item of value) {
                    if (item.name.match('^.*' + args[0] + '.*$')) {
                        resultArray.push(item);
                    }
                }
            }

            return resultArray;
        }

    }

}
</pre>

Why do you need this condition in pipe?

<pre class="lang:default decode:true " >if (args.length === 0) {
                for (let item of value) {
                    resultArray.push(item);
                }
            }</pre>

When your array of objects will be loaded it will be automatically pushed to Pipe which checks the value from your input. When input is empty the result of the Pipe will be empty too so you wont see your objects in list.

Finally working filtering pipe in Angular 2:
[![Angular2 - pipe - filter](http://fedojo.com/wp-content/uploads/2016/06/Angular2-pipe-filter.gif)](http://fedojo.com/wp-content/uploads/2016/06/Angular2-pipe-filter.gif)

After this short change the pipe works well.
Thanks 2 [Dawid Hen](http://dawidhen.pl/) for cooperation on this task!
