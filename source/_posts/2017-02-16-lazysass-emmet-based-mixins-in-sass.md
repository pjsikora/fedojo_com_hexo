---
title: LazySASS - Emmet based mixins in SASS
tags:
  - CSS
  - LazySASS
  - mixins
  - SASS
id: 1070
categories:
  - Uncategorized
date: 2017-02-16 13:55:56
---

I'm so lazy that I forgot to write any post on this website for last few months... And this post will be about my laziness as well :).
<!--more-->

Ive been working on my blog's new skin for last few months - last few months because of lots of projects on board. What I've made during working on this projects was creating own small framework. This is not that kind of frameworks which are worldwide known like Foundation or Bootstrap. It is rather related with writing own atomic mixins in SASS to smaller down the code flood in the project. I've based it on Emmet project a little bit and counting of units from Foundation project (pixels to rems).

## LazySASS The idea

Project was started during writing of [my book](https://www.packtpub.com/web-development/professional-css3) and was called as a single file [_shorts.sass](https://github.com/fedojo/usefullmixins-sass/blob/master/_fedojo.shorts.sass). It was a collection of short forms of well known CSS rules.

<pre class="line-numbers"><code class="language-sass">=tdn
    text-decoration: none

=tdu
    text-decoration: uppercase

=tac
    text-align: center

=tar
    text-align: right

=tal
    text-align: left

=ttu
    text-transform: uppercase

=ttl
    text-transform: lowercase

=di
    display: inline

=db
    display: block

=dib
    display: inline-block

=m0a
    margin: 0 auto</code></pre>

It was used to shorten the most known CSS rules in final code. For example

<pre class="line-numbers">
<code class="language-css">.className
  +di // display: inline-block
  +tac // text-align: center
  +ttu // text-transform: uppercase</code>
</pre>

Yeah... pretty small change and... unreadable. Creates additional stack of unknown rules... looks like additional new language. But who is not working with EMMET (previously known as ZenCoding)? It's not another new language just based on EMMET basics.

## Next step - LazySASS extended

Next problem which for me was the most repeatable were correct units. Ive sticked to REM instead of Pixels which made layout more adjustable. Ive been using remCalc() which was changing pixels to REM's. But the problem is repeating of this function. Lets define remCalc in SASS:
<pre class="line-numbers"><code class="language-sass">@function remCalc($value)
  $rem: $value / 16px
  @return #{$rem}rem</code>
</pre>

So each time when I wanted to apply the REM value I needed to invoke function:
<pre class="line-numbers"><code class="language-sass">h1
  font-size: remCalc(32px)</code>
</pre>
This generated:
<pre class="line-numbers"><code class="language-sass">h1 {
  font-size: 2rem;
}</code></pre>

But... what if I wanted to change the font for example to 21px and it gives me 1.3125rem? In inspector its hard to multiply it and know what was the base of this equation. Ive been moving from one unit to another but it could be based on one variable kept globally and one mixin:

<pre class="line-numbers">
<code class="language-sass">$UNIT_REM: true // pixels / rems

@function _countUnits($value)
  @if ($UNIT_REM)
    $rem: $value / 16px
    @return #{$rem}rem
  @else
    @return $value</code>
</pre>

Now we need to apply all mixins which converts pixels to rems like this:

<pre class="line-numbers">
<code class="language-sass">=mt($value)
  margin-top: _countUnits($value)

=ml($value)
  margin-left: _countUnits($value)

=mr($value)
  margin-right: _countUnits($value)

=mb($value)
  margin-bottom: _countUnits($value)</code>
</pre>

Each time when you want to change it to pixels you are setting $UNIT_REM to false. Now it is easier to inspect the size units.

## Let's summarize

So now when you want to describe element you can use code like this:
<pre class="line-numbers">
<code class="language-sass">.single_article__book__content
  +posa
  +t(0px)
  +w(470px)

.single_article__book__img
  +r(0px)
  +t(0px)
  +fr
  +posr
</code>
</pre>

It will compile to:
<pre class="line-numbers">
<code class="language-sass">.single_article__book__content {
  position: absolute;
  top: 0;
  width: 465px;
}
.single_article__book__img {
  right: 0;
  top: 0;
  float: right;
  position: relative;
}</code></pre>

...or:

    .single_article__book__content {
      position: absolute;
      top: 0rem;
      width: 29.375rem;
    }

    .single_article__book__img {
      right: 0rem;
      top: 0rem;
      float: right;
      position: relative;
    }

... in case of setted units to REM's.

## LazySASS

Code of LazySASS is [https://github.com/fedojo/LazySASS/blob/master/_shorts.sass](https://github.com/fedojo/LazySASS)!
