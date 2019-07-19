# README
Example static website built with Hugo and hosted on GitHub

## Documentation

Great documentation available at the Hugo website [here](https://gohugo.io/documentation/). The following steps are adapted from the [quickstart guide](https://gohugo.io/getting-started/quick-start/). There's also a really good youtube tutorial [here](https://www.youtube.com/watch?v=qtIqKaDlqXo&list=PLLAZ4kZ9dFpOnyRlyS-liKL5ReHDcj4G3)

## Prerequisites
* access to a terminal / command line
* git installed
* macOS (instructions will vary slightly for other operating systems)
* Homebrew package manager
* GitHub username

## Setup

### Step 1: Install Hugo
This is made simple using the Homebrew macOS package manager
```
brew install hugo
```
You can always check/verify hugo is installed by typing `which hugo`.

### Step 2: Create a site
First create a directory where your project will live, in this case `~/Projects`, then move there and run the new site command. The following will create a website in a directory called `hugo-demo`

```
cd ~/Projects
hugo new site hugo-demo
```

### Step 3: Choose a theme
Choose a theme [online](https://themes.gohugo.io/), and add it to your site. The easiest way to do this is to:
1. find the theme
2. click download to link to the theme GitHub page
3. click clone and copy the theme url to your clipboard
4. open a terminal and type the following, where `THEME_URL` is the link copied in your clipboard
```
cd ~/Projects/hugo-demo/themes/
git clone <THEME_URL>
```

### Step 4: Add some content
You can do this by manually adding a file, or with the following command
```
cd hugo_demo
hugo new posts/my-first-post.md
```
All website content is written in markdown with a toml header. This header information helps Hugo know how to organize the content.

### Step 5: Serve the webpage locally (start Hugo server)
Now you can serve the webpage on your computer, which allows you to see how it will look once its deployed on the web. It's also great for dynamically editing content.
```
hugo server -D
```
This will print a bunch of information to the terminal. Grab the line that looks like `http://localhost:1313/`, paste that into your favourite browser, and check out your new webpage!

### Step 6: Customize your site
Most of the standard customization happens in the `config.toml` file. There is a lot of information available [here](https://gohugo.io/themes/theme-components/) and in the documentation links listed in the previous section.

### Step 7: Host your site on GitHub

*These steps are for hosting from a `docs/` directory with GitHub pages - refer to the documentation for alternatives*

1. Update the base URL in your `config.toml` file. This helps Hugo correctly build the internal links between generated pages. Replace `USERNAME` with your github username.
```
baseURL = "http://<USERNAME>.github.io/hugo-demo/"
```

2. Change the directory where your full static site will be generated. This is called `public/` by default, but GitHub requires it to be called `docs/` instead. You can make the change by adding the following line to your config file:
```
publishDir = "docs"
```

3. Build your site. Open a terminal, move to your project directoy, and type `hugo` to generate your entire static webpage:
```
cd ~/Projects/hugo-demo/
hugo
```

4. Initialize a github repository on your computer with `git init`

5. Stage and commit all changes

6. Go to your GitHub account and create a new repository called `hugo-demo`. It should be public and not initialized with a readme. Copy the lines that look like the following:
```
git remote add origin https://github.com/<USERNAME>/hugo-demo.git
git push -u origin master
```
Then paste them into your terminal

7. Push changes from your project to GitHub. Your files should now appear in your newly-created GitHub repository.

8. Click on the settings tab on your repository, then scroll down to the "GitHub Pages" section. Click the dropdown under "Source" and choose the option "master branch /docs folder".

9. You should see a message: Your website is ready to be published at https://<USERNAME>.github.io/hugo-demo/". Wait a few minutes until that message goes green and reads: Your site is published at https://<USERNAME>.github.io/hugo-demo/. Click on the link to check out your new site!

### Step 8: Making changes to your website

1. Update (and save) files on your computer
2. Type `hugo server -D` to review your changes. 
3. Once you're happy, type `hugo` to generate the website
4. Commit and push your changes to GitHub