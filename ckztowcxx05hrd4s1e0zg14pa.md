## Nuxt on Netlify

My last couple of days were spent only doing one thing, converting my Server Side Rendered Nuxt.js app to a Netlify compatible (static hosting) static application. Well in theory this is a simple operation as Nuxt as a framework provides simple tooling to statically generate a static website so in theory I just have to run

`npm run generate`

and voila my SSR should be converted into a SSG output, but but but that's not very true.

Now see what happened was my app has major chunk of it as data representation, basically gets a lot of data from our database and lays it out. This was the biggest reason I went with SSR, the best way to this on pages which are just a list of documents is fetch them on the server as it is faster and the javascript bundle shipped to client is much much smaller.

So the best way of doing that for Nuxt is using a lifecycle hook called asyncData which runs on the server, now the thing is this hook is not exported to generated js. Even though is way to disable server fetching and making it client side even that woke on only if you are Nuxt in SSr mode. So I had to re-write all my asyncData hooks to mounted hooks which took me an easy couple of hours figuring this out and fixing it.

Next problem I faced was running my backend on  my express based backend on Netlify functions, well initial I thought it was as simple as setting my API folder as my functions holder with the `index.js` now that didn't give me an error, neither did it give me a response 😢. 

Some research done the line I realised I need to convert it into a Serverless-http server. After doing it both worked and did not work. 

This needed up giving me a sweet error:

```
12:09:13 AM: Request must be smaller than 69905067 bytes for the CreateFunction operation
12:09:15 AM: Request must be smaller than 69905067 bytes for the CreateFunction operation
12:09:17 AM: Request must be smaller than 69905067 bytes for the CreateFunction operation
12:09:19 AM: Request must be smaller than 69905067 bytes for the CreateFunction operation
12:09:22 AM: Request must be smaller than 69905067 bytes for the CreateFunction operation
```

every two minutes Netlify shouted at me that my express app is too big, soooooooooo
At midnight with my DBMS semester end exam tomorrow I wanted to kill myself but no I can do this is what I told myself. Then I needed up realising I already have an SSR version hosted on heroic, so I added soon CORS policies on that hosting and voila I had a version of my Application on Netlify contiously fetching data from a heroic server.


[Netlify Hosting](https://g-notify.netlify.com)
[Heroku Hosting](https://g-notify.herokuapp.com)
[Github](https://github.com/iresharma/G-notify)