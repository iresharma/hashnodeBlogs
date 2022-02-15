## Making a mass emailer

So I am the GDSC Lead for my college and as the lead one of my duties is to recruit a talented team of developers, designers and managers called the GDSC Core team.
The process was fun and after a lot of interviews I had finally decided my team, and when it came to sending out the emails, I didn't wanna manually send off 20 different mails. Plus the default gmail client doesn't let you send HTML mails anyways, so I wrote a small python script to take a jinja template render it with required info and then mail it off with the Gmail APIs.

## Product
The above story strikes an idea that just like there would be multiple people who can not send out well crafted HTML mails. So I decided to make a software solution which I named G-Notify.

### Tech specs
Being a student and still a noobie to the developer world, I wanted to learn new things with this project. So I decided with a very elaborate tech stack, here a few things could be could be removed but I got to learn a lot

- Nuxt.js --- server side rendering
- MongoDB
- Express
- Google OAuth
- Google Cloud Platform --- Storage Bucket and Gmail APIs

Some notable dependencies

- Mongoose --- for strict schemas and relations in mongoDB
- Puppeteer --- for rendering the html templates and so them (could be replaced but I wanted to try it for a long time)
- Vuetify --- for prebuilt UI components


## Features
   - Template collection --- List all public templates with ranking by likes - ✅
   - create template --- Create an HTML template on the platform - ✅
   - upload template --- Upload an HTML file as a template - ✅
   - send single template --- send one mail at a time - ✅
   - excel file for mailing list --- upload an excel file to check for emailing list - ✅
   - send multiple template --- send multiple mails at a time - ✅
   - asset management --- for people to upload files for hosting, basically a cdn mainly for images but also supports other things - ✅
   - tracking --- track if the mail was opened or not
   - handlebar templating --- use handlebar templates


### [Demo](https://g-notify.herokuapp.com) & Screenshots

***I am having huge issues running puppeteer on heroku and gcp storage bucket policies, so it'll be great if someone could help***

![Screenshot 2022-02-16 at 1.31.57 AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644955339021/L67LJ4wdV.png)


![Screenshot 2022-02-16 at 1.36.56 AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644955641532/aotlPpy8z.png)

![Screenshot 2022-02-16 at 1.35.59 AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644955646277/_rUjRabye.png)

![Screenshot 2022-02-16 at 1.35.51 AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644955653468/c3XH2pp94.png)

![Screenshot 2022-02-16 at 1.34.37 AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644955663259/wforOQjrr.png)

![Screenshot 2022-02-16 at 1.34.05 AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644955668182/bhdmbQ-un.png)
