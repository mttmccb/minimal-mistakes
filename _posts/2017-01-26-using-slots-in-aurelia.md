---
title: "Using Slots in Aurelia"
excerpt: ""
tags:
  - aurelia
  - shadow-dom
  - slot
header:
  image: /images/slots.jpg
  caption: "Photo credit: [**Ronald Saunders**](https://www.flickr.com/photos/ronsaunders47/6188663535/in/photolist-aqSw4r-35UQJb-69X25k-qDGXVP-dX9n5n-nT5HF5-iarjuS-5o8noQ-93JtxW-94V1D6-nKHCBv-epYVn3-pwPtRp-9cxyv2-qx8fcS-bwCEHi-5S64z5-4Ru6fw-6qer3E-cxoKcA-pF36ZM-71d8aY-c226ZY-keCAca-pCifQH-qBD7X2-6vunKr-bwCW9g-ztVnBG-9hHpjg-qn9X5q-4jokUv-qhXXxW-abfxKQ-qniNhM-9B1zHq-6EDhLA-8h17iU-qzkH4X-qm2mP2-duH8zL-qAJL8T-6Ez85Z-qnhBTR-8E9i4W-6P5gFb-pEMuU5-ppqA7R-GHPkuK-GHPnVr)"
---

{% include base_path %}

It's hard to believe that Shadow DOM [tutorials](https://www.html5rocks.com/en/tutorials/webcomponents/shadowdom/) for v0 of the spec first appeared in 2013 but were only implemented in Chrome and Opera. Last year v1 started making it's way into browsers and it's likely to be in them all soon. v0 to v1 was big breaking change, however I suspect only the spec editor, Hayato Ito, is interested enough to [track the differences](https://hayato.io/2016/shadowdomv1/).

Shadow DOM is one part of [Web Components](https://www.webcomponents.org/), but I want to focus on **slots**. A `slot` is placeholder within a web component that you put your own markup (including more web components!) inside. Scoped styles and having an isolated DOM is very nice to help simplify selectors in CSS and Javascript but realistically they need to be implemented by browsers. Also [**&gt;&gt;&gt;**](https://drafts.csswg.org/css-scoping/#deep-combinator) aka the *shadow-piercing descendent combinator* sounds very ominous.

## Aurelia's Implementation

Aurelia implemented [Slots](http://blog.aurelia.io/2016/05/23/aurelia-shadow-dom-v1-slots-prerelease/) in May 2016, you can read the blog but to be honest I wasn't too excited at first. As I'm now involved in developing a component library I am starting to  see the benefit, particulary over binding.

The team implemented a subset of the slot spec therefore they didn't provide a polyfill for it, they baked it into the framework. Given support was likely to be a year or 2 away it seemed like the sensible option. Even now this year is probably optimistic.

## Unnamed slot

![The Man With No Name]({{ base_path }}/images/clint-eastwood.jpg){: .align-right}

[The Man With No Name](https://en.wikipedia.org/wiki/Man_with_No_Name) played by Clint Eastwood is a lot like our unnamed slot, he had no name so we could fill ourselve.

So let's create a [Custom Element](http://aurelia.io/hub.html#/doc/article/aurelia/framework/latest/cheat-sheet/9) called `ManWithNoName` it's only job is to hold what he has to say. Since he didn't really say much I'm not sure what's going to be inside, so binding isn't a good option, so we'll see what slots can do for us.

### View - man-with-no-name.html

The view model is just a container that has a single `slot` and includes css specific to our component.

```html
<template class="ManWithNoName">
  <require from="man-with-no-name.css"></require>
  <slot></slot>
</template>
```

> Note: The class is on the `template` element because it's easier to handle animation and positioning, particularly `flex`.

### ViewModel - man-with-no-name.js

Although you could leave this as a html only component I prefer to create an empty ViewModel like so. This means I can `require` my components in the same way and if I do need some behaviour later I can add it without many changes elsewhere.

```javascript
export class ManWithNoName { }
```

### View CSS - man-with-no-name.css

Next we'll add our an amazing lightslategray (supported back to IE3 if you spell it with an 'a'!) border and give it a post-modern curve, it was modern last year ;)

```css
.ManWithNoName {
  border: 1px solid lightslategray;
  border-radius: 1rem;
  display: block;
  padding: 1rem;
  margin-bottom: 1rem;
}
```

### Using him

Now our `ManWithNoName` is just a fancy `div` that we can use like this

```html
<require from="./man-with-no-name"></require>

<man-with-no-name>Sometimes the dead can be more useful than the living.</man-with-no-name>
```

Which will render as a container with rounded corners with our text in it. It's done this because our *unnamed* slot has taken the contents of our `man-with-no-name` tag and dropped it into the `slot`.

You can play around with it on the [gist.run](https://gist.run/?id=6cf0d997a1a75b65a1aad06b10a7cda2).

The advantage of doing this will a simple custom component like this one is you can reuse it in many places and you don't have to repeat the same basic structure over and over.

## More slots!

Yes, you can create multiple slots, but now you have to give them names. So let's add some. In a lot of westerns the defining characteristics for characters are their weapons and their outfits.

### View - western-extra.html

Let's give our panel a header and body (`section` is vague, a `div` would work too).

```html
<template class="WesternExtra">
  <require from="western-extra.css"></require>
  <header class="WesternExtra-outfit">
    <slot name="outfit"></slot>
  </header>
  <section class="WesternExtra-weapon">
    <slot name="weapon"></slot>
  </section>
</template>
```

### ViewModel - western-extra.js

Another simple ViewModel.

```javascript
export class ManWithNoName { }
```

### View CSS - western-extra.css

We'll add some spacing in our outfit and weapon and a line separating them.

```css
.WesternExtra {
  border: 1px solid lightslategray;
  border-radius: 1rem;
  display: block;
  overflow: hidden;
  margin-bottom: 1rem;
}

.WesternExtra-outfit {
  background-color: darkgoldenrod;
  border-bottom: 1px solid lightslategray;
  color: white;
  padding: 1rem;
}

.WesternExtra-weapon {
  background-color: lightsteelblue;
  padding: 1rem;
}
```

> Note: I've used the [SuitCSS](https://suitcss.github.io/) naming convention as it fits really well with Aurelia's.

### Using our slots

Now our `WesternExtra` is a bit better than a `div`, we can use it like this

```html
<require from="./western-extra"></require>

<western-extra>
  <h1 slot="outfit">dead man's shoes</h1>
  <h2 slot="weapon">rifle</h2>
</western-extra>
```

As you can see rather than putting your content directly into the tag you add the `slot` attribute to an element with the name of the slot you want to put it in.

You can play around with it on this same [gist.run](https://gist.run/?id=6cf0d997a1a75b65a1aad06b10a7cda2).

Unless you have a good reason I'd try to limit the number of slots in one component, however in theory there is no limit.

![Fistful Coffins]({{ base_path }}/images/fistfulcoffins.jpg)

## But

You can't bind the slot `name` or the `slot` attribute. Probably not a big deal and it might be implemented in the future.

The contents need to be statically known, which means you can't put an `if` binding directly on the slot. `show` is fine and you can probably get around this but putting the `if` on the element inside the slot. Something like this...

```html
<template>
  <div slot="header"><div if.bind="isShown">Conditional header</div><div>
  <slot name="footer"><div if.bind="isFooter">Conditional footer</div></div>
</template>
```

## Fallback content

I won't give an example of this but you can put content inside the slot which is rendered when you don't provide any content. I've rarely used this in it's simple form and it can get a bit tricky if things are nested.

## 'Best' practices

While it's entirely possible to have slots within slots within slots within slots... don't go too far. Or at least no so far it becomes hard to trace. I can imagine you might accidently end up with 4 levels of nested slots, consider this a component smell.

Pick a naming convention and stick with it, don't be smart, try to give the slot an obvious name.

Or alternatively, avoid using multiple slots. This might seem like you're limiting yourself but it means it's very predictable. However, if you don't name the slot it should be pretty obvious where the content will be placed.

Also related, put your slots in obvious places, if they can be within a container then that can hlp you control styling.

## Use cases

You're probably looking at cases where binding doesn't make sense or you want to be flexible.

- container components, e.g. panels, call outs, message boxes
- layout components, e.g. 2 column screen layouts, a card

## Future of slots

It looks like slots (and the rest of Shadow DOM) will be implemented in browsers in the next year so we will be able to use them without any framework, although I suspect polyfills will still play a part.

Of course I'd like aurelia to add support for the most useful features without too many polyfills. Support in IDEs for validating and providing some intellisense when using components would be great, this doesn't only apply to slots but make using them much easier.

Even if you don't use aurelia you should be learning how to use slots they give you a lot of flexibility.