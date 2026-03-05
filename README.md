# Static Site Generation and Resume Hosting Guide

# Purpose

The Purpose of this README is to provide a walkthrough for using a static site generator and a forge to host a resume website. This is for someone who is interested in learning more about markdown and how to host personal sites using static site generatores and forges. No previous experience using any of these tools is necessary.

# Prerequisites

1. A GitHub account is required for this tutorial

    - Create a GitHub account [here](https://github.com/signup) if you do not already have one

2. You need a text editor for this tutorial

    - Visual Studio Code is highly recommended and will be used for the rest of the tutorial

        - Follow [this link](https://code.visualstudio.com/) and select "Download for Windows" to download and install Visual Studio Code

3. Ruby and Jekyll are both required for our static site generator to work

    - Download Ruby [here](https://rubyinstaller.org/downloads/), select "Ruby+Devkit 3.4.8-1 (x64) from the RubyInstallers section. Leave all the selections as default in the Ruby installer. The last prompt will ask you about running the ```ridk install``` step, make sure to keep this box checked.

    - Open a command prompt and type ```gem install jekyll bundler``` to install Jekyll and Bundler. Make sure Jekyll was installed properly by running ```jekyll -v```, it should return "jekyll 4.4.1"

# Instructions
## Create a Repository
1. Login to your GitHub account and navigate to your profile page at ```https://github.com/<your-username-here>```

2. Select the repositories tab near the top left corner of the page

3. Click the New button near the top right corner of the page

4. Name your repository username.github.io where username is your actual GitHub username. For example, my repository is called mateod812.github.io

## Initialize Repository
1. Within Visual Studio Code, open a new terminal

2. Change to the directory you'd like to create your local repository on by running ```cd <directory>```

3. Run ```git init <repository-name>``` and ```cd <repository-name>``` to initialize and enter the repository

4. Create a new branch by running ```git checkout --orphan main```

5. Run our static site generaotr Jekyll with this command: ```jekyll new --skip-bundle .```

6. Jekyll will create a bunch of files, locate the file titled "Gemfile" from the VS Code file exploreer and change # gem "github-pages" to gem "github-pages", group: :jekyll_plugins. Save and close the Gemfile

7. Run ```bundle install``` in your terminal

8. Add "Gemfile.lock" in a new line in the .gitignore file

9. Edit the _config.yml file to set the domain to ```https://<username>.github.io```

10. Add, commit and push your work to GitHub with the following commands

    - git add .
    - git commit -m "Initial commit"
    - git remote add origin https://github.com/<username>/<username>.github.io.git
    - git push -u origin main

11. Setup your automation for Jekyll build

    - Click Settings on your repository and find Pages under Code and automation
    - Select Deploy from a branch under Source and select "main" as the branch
    - Click save

## Creating a Page

1. Create a resume in Markdown format in a new file titled index.md

2. Edit this file in VS Code and add it to your repository

3. Make sure to have the yaml frontmatter at the top of this index.md file

4. Push your changes and confirm the build was successful

5. Navigate to ```<username>.github.io``` and make sure your index.md file is being displayed

6. You are done! Feel free to edit the index.md file as much as you want

# Further Readings/Resources

- [Jekyll](https://jekyllrb.com/)

- [Markdown Guide](https://www.markdownguide.org/)

- [Learn Git](https://git-scm.com/learn)

# FAQ

1. How can I add more than one page?
        
        Create another file and change the permalink field in the yaml frontmatter to be something different. Navigate to your site followed be /<new-page-permalink> and you will see the additional page.

2. How can I change the theme?

        Change it in Gemfile and _config.yml

# Credits

- Group 11 (Kaye Ruwe Mendoza and Andrew Driver) for their feedback during our peer review session for this assignment

- Jason Long the creator of the Cayman Jekyll theme

- The GitHub Pages team for their well written documentation on creating a GitHub Pages site using Jekyll
