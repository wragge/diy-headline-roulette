# DIY Trove Headline Roulette

[Headline Roulette](http://wraggelabs.com/shed/headline-roulette/) is a simple game that challenges you to guess the publication date of a newspaper article chosen at random from [Trove](http://trove.nla.gov.au).

Here you can build your own customised version of Headline Roulette with nothing more than a GitHub account.

For example, you might to create a version of Headline Roulette limited to articles:

* that mention **cats** or **kittens**
* that include the phrase "White Australia"
* that come from the Melbourne *Age*
* that come from your local region

It's up to you. Build a version for your workshop, class, or community. Build a version just for fun. Any search you can construct in Trove you can use to seed your game. 

## Quickstart

1. Get yourself a [GitHub](https://github.com) account (the free version is fine) and log in.
2. Get yourself a [Trove API key](http://help.nla.gov.au/trove/building-with-trove/api).
2. Come back to this page and click on the 'Fork' button (in the top right hand corner of the page) to save a copy of this repository under your own account. [More about forking](https://help.github.com/articles/fork-a-repo/).
3. Go to your account and view the repository you've just created. It will look just like this one!
4. Click on the 'Settings' tab and change the repository name to suit your game.
5. Click on the 'Code' tab. Open the `js` folder and then click on the `script.js` file to view it.
6. Click on the pencil icon to edit the file.
7. Look for the **'YOU MUST EDIT THIS SECTION'** message in the `script.js` file and add the details of your game as described in the [customisation section](#customisation-guide) below.
8. Click on the 'Commit changes' button to save your details.
9. That's it! Your hew game will be available at the address -- http://**[your Github user name]**.github.io/**[your repository name]**. For example, my user account is 'wragge' and I created a version of this repository called 'canberra-headline-roulette', so you can find it online at [http://wragge.github.io/canberra-headline-roulette/](http://wragge.github.io/canberra-headline-roulette/).

## Customisation guide

There are only two things you have to supply:

* your Trove API query
* your query

In addition, you can set:

* a tagline for your game (appears in the header)
* a byline for your game (appears in the footer)
* the messages that players see when they make a guess

There are samples of each of these (except the API key) in the `script.js` file. They all sit inside a block of code labelled 'YOU MUST EDIT THIS SECTION'.

This is the what the main configuration block looks like:

``` javascript
    // YOU MUST EDIT THIS SECTION
    // You must supply a Trove API key
    var troveAPIKey = '';
    // Either provide full API query here or include options below
    var apiQuery = '';
    // Words you want to search for -- separate multiple values with spaces, eg:
    // var keywords = 'weather wragge';
    var keywords = '';
    // How you want to combine keywords -- all, any, or phrase
    var keywordType = 'all'
    // Newspaper id numbers -- separate multiple values with spaces, eg:
    // var titles = '840 35';
    var titles = '';
    // Add a byline, eg:
    var byline = 'Created by <a href="https://timsherratt.org">Tim Sherratt</a>.'
    // var byline = '';
    // Add a tagline
    var tagline = 'How well do you know your Australian history?';
    // Leave this alone unless you're publishing on a non-https server
    var useHttps = 'true';
```

Adding your API key and setting a tagline or byline should be pretty straightforward. Just insert the values you want between the quote marks.

Setting the query your game will use to choose articles is a bit more complicated. You have two main options:

* supply a Trove API query in the form of a url
* provide keywords and/or the id numbers of particular newspapers

You'll probably only want to supply a Trove API query if you want to use a really complex query -- such as advertisements published in the Argus between 1900 and 1950. For most games you can just use the `keywords` and `titles` settings to build your query automatically.

There are three settings you can use to build your query:

* `keywords` -- the words you want to search for, separated by spaces
* `keywordType` -- how you want the keywords to be combined, expects one of: `all`, `any`, or `phrase`
* `titles` -- the id numbers of newspapers you want to search, separated by space

You don't have to use both `keywords` and `titles`, but you can combine them if you want.

The easiest place to get the id numbers of titles is from the [About digitised newspapers](http://trove.nla.gov.au/newspaper/about) page on Trove. If you click on a title, you'll open a new page which has the id of the newspaper at the end of the url. For example the page for the *Canberra Times* is:


``` http
http://trove.nla.gov.au/newspaper/title/11

```

So the id number of the *Canberra Times* is '11'.

I created a Canberra edition of Headline Roulette that sets `keywords` to 'Canberra' and includes the id for the *Canberra Times* in `titles`. Here's the config section:

``` javascript

    // YOU MUST EDIT THIS SECTION
    // You must supply a Trove API key
    var troveAPIKey = 'lb676h2eqpsrtkrc';
    // Either provide full API query here or include options below
    var apiQuery = '';
    // Words you want to search for -- separate multiple values with spaces, eg:
    // var keywords = 'weather wragge';
    var keywords = 'Canberra';
    // How you want to combine keywords -- all, any, or phrase
    var keywordType = 'all'
    // Newspaper id numbers -- separate multiple values with spaces, eg:
    // var titles = '840 35';
    var titles = '11';
    // Add a byline, eg:
    var byline = 'Created by <a href="https://timsherratt.org">Tim Sherratt</a>.'
    // var byline = '';
    // Add a tagline
    var tagline = 'How well do you know your ACT history?';
    // Leave this alone unless you're publishing on a non-https server
    var useHttps = 'true';

```

You can [try it out here](https://wragge.github.io/canberra-headline-roulette/).

Note that if you *do* supply an API query, other settings will be ignored. The easiest way to construct an API query is to use the [Trove API console](https://troveconsole.herokuapp.com/).

## Limitations

Because of the way forking works on GitHub, you can only fork a repository once into your own account. That means you can only create one game.

The easiest, but kludgiest, way around this is to create a new GitHub organisation, and then fork your second game into your new organisation's account. To create a new organisation just click on the '+' sign at the top of the screen and choose 'New organisation'.

If you're making lots of games you probably want to install Git on your local computer and follow the instructions below.

## Managing multiple games

As noted above, you can only create one game using GitHub by itself. Yes, you can a new organisation for every game, but that's going to get messy quickly. Fortunately it's easy to set things up on your local computer so that you can create as many games as you want!

The first step is to [install Git on your local computer](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

Once that's done, just follow the following steps each time you want to create a new game:

1. You'll need to [use the command line](http://lifehacker.com/5633909/who-needs-a-mouse-learn-to-use-the-command-line-for-almost-anything), so fire up a terminal.
2. On the command line type `git clone https://github.com/wragge/diy-headline-roulette.git mynewgame` -- replacing 'mynewgame' with whatever you want. This command will create a directory called `mynewgame` and copy all the files from the DIY-Headline-Roulette repository on GitHub into it.
3. Type `cd mynewgame` to move to the new directory.
4. Now you have to create a new repository in your own GitHub account. Just login to your account, click on the '+' button at the top of the page, and choose 'New repository'. Give your repository a name (probably the same as the directory you just created) and click the green 'Create repository' button.
4. Go back to your terminal and type `git remote rename origin upstream` -- this changes the name of the link to the original repository.
5. Now you need the address of your new repository. On your new repository's page you should see a url that starts with `https://github.com/` and ends in `.git` -- copy it.
6. In the terminal type `git remote add origin [your repository's url]` -- inserting the url you just copied. This will link the repository on your local machine with your new repository on GitHub.
7. Type `git push -u origin gh-pages` -- this copies the repository on your local machine to GitHub.

Now you have a choice, you can edit the files as described above in your new GitHub repository. Or you can use the text editor of your choice to modify the files on your local computer. If you edit them locally, you'll need to copy your modified files to GitHub to see your exhibition. At the terminal just type `git push origin gh-pages` -- easy!


