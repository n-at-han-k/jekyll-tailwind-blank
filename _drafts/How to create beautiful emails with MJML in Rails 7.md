
Install using:
```bash
bundle add mjml-rails
```

If you look at the git repo there is a link to an article called [using MJML in Rails](https://dev.edenspiekermann.com/2016/06/02/using-mjml-in-rails/). 

You must also install MJML’s npm package. In Rails 7 this is done via import maps.
```bash
./bin/importmap pin mjml
```

Even after this though I still had to run:
```bash
npm install mjml
```
In the root directory. The app then ran immediately.

Replace all of your `html.erb` files with `.mjml` files