# analyze-me
Analyze Me is set of packages used to assist with 
website analysis and optimization. Tasks are run to gather metrics on CSS, JS, HTML 
and factors contributing to page speed which will give you insights on how to make your
website better.

### Installation

Firstly, you need Node.js on your machine. [Node](https://nodejs.org/en/)

Next, you need Grunt installed globally:

```sh
$ npm install -g grunt-cli
```

Now, add the following files to the root of your existing project:
- package.json
- Gruntfile.js
- .travis.yml

After you've done this you can use Grunt to install your dependencies. To do this, navigate to your project's root directory on the command line/terminal and run:
```sh
$ npm install
```
The project will now have a new directory called "node_modules" with all the dependencies that are configured in the package.json file.

### Running the tasks

Tasks are run with the Grunt command:
```sh
$ grunt
```

![analyze-me](richjava.github.com/richjava.github.io/img/analyze-me.PNG)

### Threshold values, rules, and options
For some of the Grunt tasks, threshold values are set and the task's test won't pass unless these are met.

**analyze-css**

The threshold defaults can be found in the source code [here](https://github.com/DeuxHuitHuit/grunt-analyze-css/blob/master/tasks/analyze-css.js#L20).

**css-lint** 

css-lint uses rules instead of threshold values. The default functionality is that if any of the rules aren't met, a warning will be displayed. The rules are on the [Github repository readme](https://github.com/gruntjs/grunt-contrib-csslint) and an explanation of those rules are [here](https://github.com/CSSLint/csslint/wiki/Rules).

**jshint**
In jshint, you can configure [options](http://jslinterrors.com/options/), which are similar to rules. A list of JSHint errors is [here](http://jslinterrors.com/?linter=jshint).

**htmlhint**

htmlhint uses the following [rules](https://github.com/yaniswang/HTMLHint/wiki/Rules). The default value for all the rules is: true 

**grunt-pagespeed**

Google Pagespeed uses a threshold overall Speed score to determine whether the site being assessed passed the test or not. At the time of writing, there is a known issue with threshold scores in grunt-pagespeed (the Grunt processes would stop if the site didn't meet the pagespeed threshold - See [here](https://github.com/jrcryer/grunt-pagespeed/issues/26)), so it's recommended not to set it.

### Reports
Currently, analyze-me has support for writing the following reports to a "reports" directory in the project root:
* csslint
    * csslint-checkstyle-xml-report.xml
    * csslint-compact-report.xml
    * csslint-csslint-xml-report.xml
    * csslint-junit-xml-report.xml
    * csslint-lint-xml-report.xml
    * csslint-text-report.xml
* jshint
    * jshint-report.html


### Travis CI
A .travis.yml file is included, so you can use [Travis CI](https://travis-ci.org) to build your project on every git push to Github, and you can analyze the print outs from your tasks from there too.

From your Travis CI dashboard, you can get the markdown for a build status image to add to your Github README so you and others can see if your Grunt task tests are passing from there.

### Example
An example app that uses analyze-me can be found [here](https://github.com/richjava/analyze-me-html5boilerplate).