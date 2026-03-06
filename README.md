# Static Site Generation and Resume Hosting Guide

# Purpose

The purpose of this README is to provide a walkthrough for using a static site generator and a forge to host a personal website. This is for anyone who is interested in learning more about Markdown and how to host personal sites using static site generators and forges. It is primarily meant for readers who have at least some basic command line knowledge. No previous experience using any of the other tools is necessary, there will be instructions and links to external resources along the way.

Here is an [example](https://mateod812.github.io/) of what you can expect to be able to build after following this guide!

# Prerequisites

1. A GitHub account is required for this tutorial

    - Create a GitHub account [here](https://github.com/signup) if you do not already have one

2. You need a text editor for this tutorial

    - Visual Studio Code is highly recommended and will be used for the rest of the tutorial

        - Click [this link](https://code.visualstudio.com/) and select **Download for Windows** to download and install Visual Studio Code

3. Ruby and Jekyll are both required for our static site generator to work

    - Download Ruby [here](https://rubyinstaller.org/downloads/), select **Ruby+Devkit 3.4.8-1 (x64)** from the Ruby Installers section. 
    
    - Leave all the selections as default in the Ruby installer. The last prompt will ask you about running the ```ridk install``` step, make sure to keep **this box** checked.

    - Open a **command prompt** and type ```gem install jekyll bundler``` to install Jekyll and Bundler. 
    
    - Make sure **Jekyll** was installed properly by running ```jekyll -v```, it should return "jekyll 4.4.1"

4. The version control software Git is required for this guide

    - Download Git [here](https://git-scm.com/install/windows) and click on **the first download link** under the **Windows** tab to install the latest version of Git for Windows.

# Instructions

Andrew Etter's book **Modern Technical Writing** recommends using simple tools such as Markdown, distributed version control systems like Git, and static site generators like Jekyll, when writing technical documentation. These tools make documentation easier to maintain, contribute to, and understand. The following guide applies these principles by providing a walkthrough on hosting Markdown formatted files using GitHub Pages and Jekyll.

## Create a Repository
1. Login to your GitHub account and navigate to your **profile page** at ```https://github.com/<your-username-here>```.

2. Select the **repositories** tab near the top left corner of the page. ![](/images/repo.png)

3. Click the **New** button near the top right corner of the page. ![](/images/new.png)

4. Name your repository "username.github.io" where username is your actual GitHub username. 
    - For example, my repository is called mateod812.github.io

5. Keep the visibility of the repository on **Public** or else GitHub Pages will not work.

## Initialize Repository
1. Open **Visual Studio Code** 

2. Open a **new terminal** 

![](/images/terminal.png)

3. Run ```cd <directory>``` in the terminal, where ```<directory>``` is the directory that you would like to create your local repository on.

4. Run ```git init <repository-name>``` to initialize the repository.

5. Run ```cd <repository-name>``` to enter the repository directory.

6. Run ```git checkout --orphan main``` to create a **new main branch** for your repository.

7. Run our static site generator Jekyll with this command: ```jekyll new --skip-bundle .```. Jekyll will create a bunch of files that we will use for editing and creating our website.

8. Locate the file titled "Gemfile" from the VS Code file explorer. 

![](/images/gem.png)

9. Delete **this line**: ```# gem "github-pages"``` from the Gemfile.

10. Add **this line**: ```gem "github-pages", group: :jekyll_plugins``` to the Gemfile.

11. Save and close **the Gemfile**.

12. Run ```bundle install``` in your terminal

13. Add ```Gemfile.lock``` in a new line in **the .gitignore file**.

14. Edit the **url field** in the _config.yml file to be ```https://<username>.github.io``` where username is your actual GitHub username.

15. Add your work to your repository with this command: ```git add .```.

16. Commit your work to your repository with this command: ```git commit -m "Initial commit"```.

17. Run ```git remote add origin https://github.com/<username>/<username>.github.io.git``` to link your local repository to the one you created on GitHub.

18. Run ```git push -u origin main``` to push your work to GitHub. The files from your local repository should now appear on your GitHub repository.

19. Click **Settings** on the page for your GitHub repository.

20. Find and click **Pages** under the **Code and automation** section.

21. Select **Deploy from a branch** from the dropdown menu under **Source**.

22. Select **main** as the branch that your GitHub Pages site will be built from

23. Click **Save** ![](/images/pages.png)

## Creating a Page

1. Create a **new file** in your local repository folder called ```index.md```

2. Add some markdown formatted **content** to this file. For the purposes of this tutorial, I recreated my resume in markdown format. Markdown is used due to its simplicity, flexibility and readability. 
    - [Jump ahead](#markdown-guide) for a Markdown refresher/tutorial

3. Make sure you have the YAML frontmatter at the very top of this index.md file. It should look like this: ![](/images/yaml.png)

4. Add **your changes** with ```git add .```

5. Commit **your changes** with ```git commit -m "Adding a new page"```

6. Push **your changes** with ```git push```

7. Navigate to ```https://<username>.github.io``` in a web browser. 

8. Make sure your **index.md file** is being displayed on the website.

9. You are done! Feel free to edit the index.md file as much as you want and check out some further readings/resources to tackle more advanced topics.

# Further Readings/Resources

### Jekyll
Here is a link to the official [Jekyll](https://jekyllrb.com/) website where you can further familiarize yourself with how Jekyll works. There is a docs section which provides you with some more useful Jekyll basics in regards to getting started with using it. There is also a resources section where you can dig deeper into what Jekyll has to offer with its various themes, plugins, guides and many other things!

### Markdown Guide
This [Markdown Guide](https://www.markdownguide.org/) is useful if you want to get some more practice with writing documents in markdown. It has cheat sheets, basic syntax, tutorials, and everything else you need to learn, practice and master markdown.

### Learn Git
Git has a [learning section](https://git-scm.com/learn) on their official website which has some very useful resources and guides for learning git. There are cheat sheets, short video tutorials and plenty of external links to other tutorials, books, videos and courses.

### GitHub Pages
There are plenty of additional articles and guides for diving deeper into using GitHub Pages on the [documentation page](https://docs.github.com/en/pages) of GitHub. Here you can learn more about GitHub Pages and learn how to setup things like custom domains for your GitHub Pages website.

# FAQ

### Why are my changes not being applied to my website?
        
- Make sure you committed and pushed your changes to your GitHub repository. Once you confirm that the changes were committed and pushed, check the "Actions" tab of your repository and make sure the workflow for your Jekyll/GitHub Pages build has completed successfully. This workflow can take a few minutes to run.

### How can I change the theme of my website?

- Add **this line**:  ```remote_theme: pages-themes/<theme-name-here>``` to your _config.yml file and replace ```<theme-name-here>``` with the name of a theme that is supported by the remote_theme plugin for Jekyll. A list of supported themes is found [here](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-a-theme-to-your-github-pages-site-using-jekyll). Commit and push your changes to GitHub and GitHub Pages will rebuild your website with the new theme applied

### Why do I have to use Git to setup my personal website?

- It is very important to use version control software like Git because it allows you to store backups of your work and keep track of all changes made to your work. Without version control software like Git, a small two second mistake can turn into hours of recovery. By using Git, you allow yourself to recover from mistakes quickly and easily.

# Credits

- Group 11 of COMP 2600 (Kaye Ruwe Mendoza and Andrew Driver) for their feedback during our peer review session for this assignment

- Jason Long the creator of the [Cayman](https://github.com/pages-themes/cayman) Jekyll theme

- The GitHub Pages team for their well written [documentation](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll) on creating a GitHub Pages site using Jekyll
