# Local deployment

This blog is configured to run on **Ruby 3.2.2** using **Jekyll**. Follow these steps to preview your changes locally before pushing to GitHub.

## 🛠 Prerequisites

Ensure your environment is using the correct Ruby version:
* **Ruby:** `3.2.2`
* **Bundler:** `2.x.x` (via the alias in your `~/.zshrc`)

```bash
ruby -v
bundle -v
```

## How to Serve the Blog

### 1. Install Dependencies
If you have just cloned the repo, updated the Gemfile, or deleted your Gemfile.lock, run:
`bundle install`

### 2. Start the Local Server
Run the following command to build the site and launch the local staging server:

`bundle exec jekyll serve`

### 3. View the Site
Once the terminal displays Server address: http://127.0.0.1:4000/, open your browser to:
http://localhost:4000

To shut down the local preview and free up the port, go to your terminal and press:
Control + C


### Template

Based on the blog template at http://github.com/mojombo/jekyll, https://tom.preston-werner.com/.
