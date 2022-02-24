## Keep Static Site up to Date With Hashnode Blog

Two of the best features of Hashnode are it's GraphQL API, and the ability to automatically backup copies of your blog posts, and store them as markdown files in your own GitHub repo.

Sure you can setup a custom domain and add your own styling to your blog, but for full control I prefer to [grab data from the Hashnode GraphQL API](https://catalins.tech/hashnode-api-how-to-display-your-blog-articles-on-your-portfolio-page), to display it on my portfolio.

### What about other hosts?

My portfolio is a static site hosted on Netlify, but this same general idea should be applicable to most static site hosts, with minor changes.

The following assumes you have a static site pulling data from Hashnode's API, and you have setup your blog to [automatically backup all your posts to GitHub](https://support.hashnode.com/docs/github-backup).

### Netlify Build Hook

1. Login to your Netlify account 
2. Select the site you want to build
3. Select `Site settings`
4. In the sidebar select `Build & deploy`
5. Scroll down to "Build hooks"
6. Select `Add build hook`
7. Enter a hook name
8. Select branch to build
9. Copy the build hook url

### GitHub Actions

In the repo you created to backup your markdown files, you should create a YAML file in ./github/workflows/. For example I use

```
.github/workflows/build.yml

```

And place the following into the file

```
name: Netlify Build

on:
  push:
    branches: [ main ]

jobs:
  build:
    name: Request Netlify Webhook
    runs-on: ubuntu-latest
    steps:
      - name: Curl request
        run: curl -X POST -d {} YOUR HOOK URL HERE
```

This will trigger a request to the build hook URL you created earlier, any time there are changes pushed to the main branch of the Hashnode backup repository.

Additional information about [Netlify build hooks](https://docs.netlify.com/configure-builds/build-hooks/) and [GitHub Actions](https://docs.github.com/en/actions) can be found in their supporting documentation.





