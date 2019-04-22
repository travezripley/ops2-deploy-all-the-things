# Deploy All The Things
Third Project in the OPS200 * Module @ San Diego Code School

#Author - Michel Roberts JR.

#Modified by Travis Ripley, * Started Monday April 22th, 2019 10:30am
## You don't got to love it, because the hood's gon' love it. 


### Introduction

In this project, we're going to show you how to deploy your React applications to [Heroku](https://heroku.com). Up until this point, we've asked you to use [Now](https://now.sh) to push your work live.

First, we need to perform the usual, repeatable steps to start a new project. Clone the project from [github](https://github.com/SanDiegoCodeSchool/ops200-deploy-all-the-things)

## Setup

Sign up for a free [Heroku](https://heroku.com) account and enter a payment method to verify your account and give you the ability to deploy unlimited free apps. Your card will not be charged unless you  increase the size of a Dyno (which is very difficult to do by accident).

Next, follow the instructions in [this guide](https://devcenter.heroku.com/articles/heroku-cli) to install the Heroku CLI - a tool we'll use to talk to Heroku via CLI. 

Once you've downloaded and installed the tool, you need to login to Heroku via CLI. This is done because we will be executing commands that are specific to your account. Open a terminal and run the following command to login to Heroku in your CLI:

```bash
$ heroku login

# Enter credentials and 2FA code if requested
```

After you've logged in, you're ready for the next step.

## Deploy your first app

We have provided an empty React project that simply renders "My first Heroku app" to the screen, in this section we'll push it to Heroku using the CLI tools and Git.

The first thing we need to do is create an App on Heroku. Open up a command line interface and enter the following five commands:

```bash
# Navigate to the correct folder
$ cd ~/oca/startnow-ops200-deploy-all-the-things

# Initialize a git repository within the project folder
$ git init

# Add all changes to staging area
$ git add .

# Commit changes to the repository
$ git commit -m "Initial Commit"

# Create a new Heroku app
$ heroku apps:create
```

If that worked, you should see the following output (your website will be called something else as Heroku generates a random name for your project when you run `heroku apps:create`.)

![](https://i.imgur.com/aDvO5ot.png)

Next, run `heroku open` in the terminal to ensure Heroku has successfully created your app. If it worked you should see a page similar to this:

![](https://i.imgur.com/GMecfBk.png)

This page tells you that Heroku has provided a placeholder ready for you to deploy your app into. To actually push your app to Heroku,  return to the terminal (ensuring you have used `cd` to navigate to `~/oca/startnow-ops200-deploy-all-the-things`) and run the familiar `git push` command, but to the `heroku` remote instead of `origin`.

```bash
$ git push heroku master
```

This will trigger Heroku to run the buildpack for your application to retrieve `npm` dependencies, output generated assets or compiled code and more.

To check that the site has been deployed, return to the terminal and run `heroku open` to open your website in Google Chrome. You may see something like this...

![](https://i.imgur.com/Rcc00nH.png)

If that's the case and you don't see any content, then the site's not working. This is a good chance to practice "putting some fires out". We're going to give you some hints - but it's up to you to get the page to render. And no, "it works on my machine" is not sufficient :o)

By the end of your debugging journey, your website should look like this:

![](https://i.imgur.com/AvwQQ1D.png)

Hints:

- Check Chrome Development Tools
- Run `heroku logs --tail` to inspect remote logs (and see what happened)
- Research details about the Heroku build process for NodeJS applications.

> Once you have the example app up and running - you're officially a member of the "doin' it live" club. Congrats!

## Deploy all the things

Next, let's push some more apps. The React apps you've been working (including your hackathon project) seem like good candidates.

Upload the following apps..

- [ ] REACT100 - Change Calculator
- [ ] REACT100 - Mortage Calculator
- [ ] REACT100 - Top Spots
- [ ] REACT100 - VSTDA
- [ ] REACT100 - Hackathon

> NOTE: Make sure that in each project you check the `package.json` file and
> that under "scripts" and "start" the command includes "npm run build"
> ```json
> {
>  "scripts": {
>    "start": "node server",
>    "build": "..."
> }
> ```
> `package.json` above would need to be changed to:
> ```json
> {
>   "scripts": {
>     "start": "npm run build && node server",
>     "build": "..."
> }
> ```

..using the following process:

```bash
# Navigate to the project
$ cd ~/oca/startnow-react100-<project-name>

# Commit any outstanding work
$ git add . && git commit -m "Ready for deployment"

# Create a heroku app with a custom name.
# (Initials followed by project name works.)
$ heroku apps:create <initials>-<project-name>

# Normally when you deploy, you would NOT set production modes to false
# To ease the process run this command to have heroku also download your devDependencies
$ heroku config:set NPM_CONFIG_PRODUCTION=false -a <app-name>

# Push a release
$ git push heroku master

# To debug when things go wrong
$ heroku logs --tail
```

## Submission/Running the Tests

To run the tests and submit this assignment for grading, you will need to enter the URL of each of your REACT apps in the `config.json` file found in the project folder for this workshop.

```js
{
  "first_app": "",
  "change_calculator": "",
  "mortgage_calculator": "",
  "top_spots": "",
  "vstda": ""
}
```

Once these values are provided, open a terminal and run the following commands to execute the tests.

```bash
# Navigate to this project.
$ cd ~/oca/startnow-ops200-deploy-all-the-things

# Run the tests.
$ npm test
```

## Exit Criteria
- Push the example app to Heroku
- Push Change Calculator to Heroku
- Push Mortgage Calculator to Heroku
- Push Top Spots to Heroku
- Push VSTDA to Heroku
- Push your hackathon project to Heroku
- Follow the instructions above to submit the assignment

##