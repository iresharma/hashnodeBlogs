## Best documentation award goes to NUXT.js

# Best documentation award goes to NUXT.js

Ooof that's a big claim, well yes but just listen me out.
I have been writing Vue.js code for almost a year and I have made a lot of projects with Vue not just personal but also a couple of production projects at my internship.
That's enough prefaces, I am currently working in an edtech startup and have been exploring a lot of new things, SSR (Server-Side-Rendering) with Nuxt.js being one of then.

### Why Server Side Rendering ?

SSR or server side rendering, according to me is very useful when you have app that shows a lot data on the frontend so let's an app which serves the main purpose of showing you all the stats for your company or an app lists out nearby restaurants  or something.
This is because if your app is a server side rendered all your data is already there and in place instead of showing a table a with a loader it presents you with a table straight away, another use case for SSR is if your user base comprises of people who would have phones/pcs that might be able to or be very slow in rendering js that is delivered by modern web frameworks like React, Vue or Angular


**PS I am new to the SSR world, this is my basic understanding of the tech *I'd love to get corrected in the comments❤️***

### Our service and why SSR ?
Well as I mentioned I am working on an edtech startup and hence we have an app for it. Now we need a portal check our user data, generate reports and have a place to enter questions and content.
So if you think of it the frontend basically has two jobs:
   - Show data
   - Input for educational content

So the major part is data showcase we opted for SSR.

## Nuxt Basics
Well SSR application structure(or atleast for Nuxt) is very very different, instead  of over general src and dist folders you are represented with a huge folder structure (given you use `npx create-nuxt-app <project-name>`)

- assets
- components
- layouts
- middleware
- pages
- plugins
- static
- store

#### Assets
Well not a lot to talk about assets is the folder that contains your assets. 
`'~/assets/'` here's an awesome thing with Nuxt, it already has aliases set for you

#### Components
Love of modern frontend frameworks ***components*** well this is the place where you keep all your components global or not (maybe not but that's what we are doing right now)

#### layout
This is where my new love for nuxt starts, i used to hate writing way too many v-if statements in my App.vue file and have a huge set of spaghetti code which might be a nightmare to get back to fix bugs or add features. But Iresh what is it ??
Well Vue.js developers here's the thing files in the layout folder contains your layouts
So let's say you have a navbar which is supposed show Sign in and Register buttons only, when the user is not logged in but you wanna show a lot more options along with a sidebar ?? Well now you can have the navbar with more options and the sidebar in the `~/layout/default.vue` as that's the default file that loads your UI unless specified to do something else.
And for your constrained view you can make a new file in the layouts folder called `auth.js` or anything and specific that in your login/register or relevant pages.
Here's a small example from my current project

```html
<!-- default.vue -->
<template>
  <div>
    <sideBar />
    <vs-row style="height: 100vh">
      <vs-col :offset="side ? 2 : 0" :w="side ? 10 : 12">
        <navBar />
        <Nuxt />
        <cusFooter />
      </vs-col>
    </vs-row>
  </div>
</template>
```

```html
<!-- auth.vue -->
<template>
  <div>
    <navBar />
    <Nuxt />
    <cusFooter />
  </div>
</template>
```
** So the `<Nuxt />` component that you see is responsible for rendering your pages, we'll talk about that later **

Now to render the auth layout when you are on the login/register screen all you have to do is add a property called layout in the export object of your page

```javascript
export default {
  layout: 'auth',
}
```

Additionally you can also add an `error.vue` file which gives you access to the error object and the UI there would be rendered in case you face an error, **An important thing to note you are not supposed to put the `<Nuxt />` component there as you would not want your UI to render if there's an error**


#### Middlewares
The files here are supposed to have a butch of middlewares, basically functions that you'd want to run write before the user changes routes. An example would be sending an auth call to check your JWT token or basically any kind of auth that you are using. I haven't played a lot with this yet.

#### Pages
This folder would correspond to the Views page in your vue.js project, just with add benefit that you don't need to write your route file, which may /may not be a benefit given your use case.
A few things to remember the folder structure defines your router as in,
a file `login.vue` could correspond to `baseurl/login` but a file `Auth/login` would correspond to `baseurl/Auth/login`. Additional this comes with a index.vue file which corresponds to the home route.

#### Plugins
Another great feature of nuxt.js is that it supports something called modules/plugins which is essentially wrappers for various commonly used node_modules which are tuned for use with SSR and nuxt specifically. A few plugins that we are using include firebase, axios, content, vuesax, etc.
Here's the [official list of nuxt modules](https://modules.nuxtjs.org/).
You setup, initialize and customize how your modules work in the nuxt.config.js file.

#### Static
This folder doesn't look like something very fancy but this here to basically keep all your static that will be available in the browser.
**Note you are not supposed to keep any confidential files here**

#### Store
This folder is entirely dedicated to the Vuex store and only exists if you add the vuex module. A few differences  in the normal vuex uses in vanilla Vue.js and nuxt is that here you need to export your state, mutations, actions and all separately from the file instead of exporting a single Vuex object. Plus Nuxt support vuex modules out of the box just create a new file in the store folder and you have a new vuex module


### Well disclosure time all of this I leanrt directly from the nuxtjs official documentation, hence **best documentation**.

Also I have been writing a few flutter blogs here but now that I jumped into Nuxt.js It'll be a fun ride and I wanna share this experience with everyone so I'd be writing more blogs about it so do follow. 