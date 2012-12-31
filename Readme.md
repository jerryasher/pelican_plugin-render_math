Latex Plugin For Pelican
========================

This plugin allows you to write mathematical equations in your articles using Latex.
It uses the MathJax Latex JavaScript library to render latex that is embedded in
between `$..$` for inline math and `$$..$$` for displayed math. It also allows for 
writing equations in by using `\begin{equation}`...`\end{equation}`.

Settings
--------
To enable, ensure that the plugin is installed somewhere that is accessible.
Then use as follows by adding to the settings file:

    PLUGINS = ["latex"]

to your settings.py

Be careful: Not loading the plugin is easy to do, and difficult to detect. To
make life easier, find where pelican is installed, and then copy the plugin
there. An easy way to find where pelican is installed is to verbose list the
available themes by typing `pelican-themes -l -v`. 

Once the pelican folder is found, copy plugin to the `plugins` folder. Then 
add to settings file like this:

    PLUGINS = ["pelican.plugins.latex"]

Usage
-----
Add the following to your template file between the `<head>` parameters (for
the NotMyIdea template, this file is base.html)

    {% if article and article.latex %}
        {{ article.latex }}
    {% endif %}

Now latex will be embedded in every article. If however you want latex only for
selected articles, then in settings.py, add

    LATEX = 'article'

And in each article, add the metadata key `latex:`. For example, with the above
settings, creating an article that I want to render latex math, I would just 
include 'Latex' as part of the metadata without any value:

    Date: 1 sep 2012
    Status: draft
    Latex:

Example
-------

The two most popular ways to embed latex are as follows:

1. **Inline** - between `$..$`, for example, `$`x^2`$`.
2. **Displayed Math** - between `$$`..`$$`, for example, `$$`x^2`$$`.
3. **Equations** - between `\begin` and `\end`, for example, `begin{equation}` x^2 `\end{equation}`.
    
To see an example of this plugin in action, look at [this article](http://doctrina.org/How-RSA-Works-With-Examples.html). To see how
this plugin works with a template, look at [this template](https://github.com/barrysteyn/pelican_theme-personal_blog).
