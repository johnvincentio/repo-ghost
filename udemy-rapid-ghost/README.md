
# Ghost
[Ghost](https://ghost.org/)

[Ghost github](https://github.com/TryGhost/Ghost)

[Ghost github wiki](https://github.com/TryGhost/Ghost/wiki)

[Ghost Dev](https://dev.ghost.org/)

## Ghost Account
From [Ghost](https://ghost.org/), select Sign in

Sign Up


## Download

[Download](https://ghost.org/developers)

## Mac Install & Start
Unzip and copy to
/Users/jv/Desktop/MyDevelopment/github/cms/repo-ghost/udemy-rapid-ghost/rapidghost

cd /Users/jv/Desktop/MyDevelopment/github/cms/repo-ghost/udemy-rapid-ghost/rapidghost

npm install

npm start

Url configured as: http://localhost:2368

From a browser:
http://localhost:2368 

## Create a Blog
http://localhost:2368/ghost/setup/one/

Create your account:

Do not invite others

## Upgrade Ghost
http://localhost:2368/ghost/settings/labs/

Export (file with blog settings and data)

More to come here...

## Configuring a Blog

see config.js

runs on a development environment by default.

production:

updateCheck: true (default) will check for Ghost updates.
fileStorage: true (default) will store images etc locally.

## Setting up the email

Sign up with [Mailgun](https://www.mailgun.com/) and login.

From mailgun dashboard:

```
Domains, select Domain name
Copy: Default SMTP login
Paste: mail: auth: user

Copy: Default password
Paste: mail: auth: pass
```

```
Config.js:
uncomment development section
```

### Reset password to ensure email is working

```
Stop Ghost and restart
npm start

http://localhost:2368/ghost
Signout (top left nav)

Sign in form:
john.vincent.internet@gmail.com
Forgot?

Verify receive email to reset password. Do not need to reset, just verify can reset if password is lost
```

## Keep your Blog running

Use PM2, a production process manager for Node.js applications with a built-in load balancer.

```
Install PM2:
cd repo-ghost/udemy-rapid-ghost/rapidghost
npm install -g

pm2 -v

pm2 start index.js

verify is running:
http://localhost:2368/
```

```
Useful commands:
pm2 list

pm2 stop <process-id>
or:
pm2 stop all

pm2 restart <process-id>
or:
pm2 restart all

pm2 delete <process-id>
```

```
Start in Production Mode:
NODE_ENV=production pm2 start index.js --name rapidghost

```

```
If make a change to your blog, you must restart:

pm2 restart all
```

## Blog and User Settings

```
Login in Ghost blog:
http://localhost:2368/ghost
john.vincent.internet@gmail.com

Settings, General

Team
Select User
Upload Image
Upload cover photo

```

## Ghost Themes

Themes use [Handlebars](http://handlebarsjs.com/)

```
see:
/Users/jv/Desktop/MyDevelopment/github/cms/repo-ghost/udemy-rapid-ghost/rapidghost/content/themes/casper

default.hbs is header and footer
index.hbs is main part of the blog
post.hbs is template for a single post
tag.hbs creates a list of posts by tag

assets:
css, fonts, js

partials: loop.hbs

```

## Finding Themes

[Ghost Marketplace](http://marketplace.ghost.org/)

```
Not free:
https://themeforest.net/item/ivy-responsive-masonry-ghost-theme/9482468?s_rank=9

Free:
https://github.com/daanbeverdam/buster
https://github.com/haydenbleasel/ghost-themes
https://github.com/chris-brown/Masonry-Ghost-Theme

Downloaded to:
/Users/jv/Desktop/MyDevelopment/github/cms/repo-ghost/udemy-rapid-ghost/downloaded-themes/buster-master


```

## Install Theme

```
Copy:
cms/repo-ghost/udemy-rapid-ghost/downloaded-themes/Masonry-Ghost-Theme
to:
/Users/jv/Desktop/MyDevelopment/github/cms/repo-ghost/udemy-rapid-ghost/rapidghost/content/themes/Masonry-Ghost-Theme

Restart Ghost:
cd cms/repo-ghost/udemy-rapid-ghost/rapidghost
pm2 start index.js

or, if still running in PM2:
pm2 restart all
```

## Swap Theme

```
Login in Ghost blog:
http://localhost:2368/ghost

Settings, General

Activate theme
Save

```

## Adding Discus Comments

[Disqus](https://disqus.com/)

Signup for an account.

I want to install Disqus on my site.

* Website name: internet-developer
* Category: Tech
* Create Site>

Got it. Let's get started.

* Ghost


Ghost install instructions:

* View the Universal Embed Code.

```
<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = PAGE_URL;  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://internet-developer.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
```

* /Users/jv/Desktop/MyDevelopment/github/cms/repo-ghost/udemy-rapid-ghost/rapidghost/content/themes/Masonry-Ghost-Theme-master/post.hbs

* * replace lines 31 & 32 with code above.
* restart Ghost


Your website: internet-developer.disqus.com
Disqus shortname: internet-developer
Organization admin: john.vincent.internet@gmail.com (add another admin)


Configure Disqus.
Use the defaults.

# Adding Google Analytics
Login.

Admin, Account Settings
Click Account name,
From dropdown, Create new account.

Account name: Blogging
Website name: Ghost Blog
Website url: www.internet-developer.com
Get Tracking Id>

Shows Website Tracking Code:
Copy the code

Edit the default.hbs file.

/Users/jv/Desktop/MyDevelopment/github/cms/repo-ghost/udemy-rapid-ghost/rapidghost/content/themes/Masonry-Ghost-Theme-master/default.hbs

Paste the code before the closing body tag and before the script includes.
Save.

Restart Ghost.

















