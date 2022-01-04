---
layout: post
title:  "Hosting with github page using jekyll"
date:   2022-01-07 20:42:57 +0545
categories: how to host using jekyll to github page
---

# Software you need

Hosting your page with github is easy and free so what is stopping you from having your own website? maybe a good tutorial on how to do so.

Let me walk you through the way where you can create and host your website for free.

- Jekyll
   Jekyll is an static site generator which helps to transform your plain text into static websites and blogs.
   You can install jekyll and its dependences following the documentation at [jekyll](https://jekyllrb.com/docs/installation/){:target:"_blank"}.

   jekyll can be installed in differnet platform following the link based on your machine.

   - [For Windows](https://jekyllrb.com/docs/installation/windows/){:target:"_blank"}
   - [For Ubuntu](https://jekyllrb.com/docs/installation/ubuntu/){:target:"_blank"}
   - [For MacOs](https://jekyllrb.com/docs/installation/macos/){:target:"_blank"}
   - [Other linux Distro](https://jekyllrb.com/docs/installation/other-linux/){:target:"_blank"}

- Git client and Github account
  Git is software for tracking changes in any set of files, and it helps to move your code from local machine to github.
  Github will give storage to store your code. You can use either terminal or a graphical based git client to connect to github. You can install git client from [here](https://git-scm.com/downloads).

# Steps after downloading

## Run jekyll

To run jekyll you need to go to the folder you have installed jekyll and open the terminal where you paste the following command ``` jekyll serve ```. After that you can visit to [http://127.0.0.1:4000](http://127.0.0.1:4000){:target:"_blank"} to see the your site in your machine.

You can customize and change the content of your site following the jekyll documentaion.


## Push your code to github

If you do not have a github account create it by going to [Github](https://github.com/register).

Then create a new repository by clicking the new button on the dashboard.

![Create Repository Button](/images/create-repo-button.png)

Put your username.github.io as the repository name, make it public and press create.

![Create Repository Button](/images/repo-name.png)

After creating the repository you have to push the jekyll in your local machine to the git repository.

If you are using git client then open the command line tool in the folder you have installed jekyll then run following commands or will see the following commands in new page so follow the instruction.


```

git init

git commit -m "your commit message"

git branch -M main

git remote add origin https://github.com/YourUserName/YourRepositoryName.git

git push -u origin main

```

After pushing your code to github your website will be live at yourusername.github.io and can view

From Now on you can just make the changes and push it to github to update the content


# Using custom domain in your github page

You can change the domain of this website with any custom domain you own for that you need to login into the domain provider and add a new dns record with type CNAME name as your domain and target as yourusername.github.io

This will take some time to setup your website properly and can access your github page using the custom domain


















