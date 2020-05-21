<p align="center"><a href="https://sourcethemes.com/academic/" target="_blank" rel="noopener"><img src="https://sourcethemes.com/academic/img/logo_200px.png" alt="Academic logo"></a></p>

# How to update the site
Go to [Github](https://github.com/) and register for an account if you have not done so already. Github encourage using your real name as your username, and this can help your Github URL (which you will be assigned later) to have a professional appearance.

[Install Git](https://help.github.com/en/github/getting-started-with-github/set-up-git) if it’s not already present on your system. You can check by running git --version in your Command Prompt/Terminal app.

Once you have created your Github account and setup Git on your computer, we will create two new repositories (often abbreviated as repos) on Github with the following names:

- `academic-kickstart` or any other name you like - we will save your content to this repo
- `<USERNAME>.github.io` where `<USERNAME>` is your Github username - we will save the generated website to this repo

To create the `<USERNAME>.github.io` repository, click the “+” icon in the top right corner and then choose “New Repository”.

To create the `academic-kickstart` repository, [fork](https://github.com/sourcethemes/academic-kickstart#fork-destination-box) the Academic Kickstart repository and clone your fork with Git (download it to your computer) by replacing `<USERNAME>` in the following command with your Github username:
  ```bash
  git clone https://github.com/<USERNAME>/academic-kickstart.git My_Website
  cd My_Website
  git submodule update --init --recursive
  ```

In your `config.toml` file, set `baseurl = "https://<USERNAME>.github.io/"`, where `<USERNAME>` is your Github username. Stop Hugo if it’s running and delete the `public` directory if it exists (by typing `rm -r public/`).

Add your .github.io repository into a submodule in a folder named public, replacing with your Github username:
  ```bash
  git submodule add -f -b master https://github.com/<USERNAME>/<USERNAME>.github.io.git public
  ```
Add everything to your local git repository and push it up to your remote repository on GitHub:

  ```bash
  git add .
  git commit -m "Initial commit"
  git push -u origin master
  ```

Whilst running the above commands you may be prompted for your Github username and password.

Next, regenerate your website’s HTML code by running Hugo and uploading the public submodule to GitHub:
  ```bash
  hugo
  cd public
  git add .
  git commit -m "Build website"
  git push origin master
  cd ..
  ```
Once Git has finished uploading your site to Github, you can open your new https://<USERNAME>.github.io website in your browser, substituting with your Github username.
