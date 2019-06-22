# pandachartstore

Chartstore is designed to be a dynamically updatable repo for charts used in the [Pontificating Panda Chartbook](https://djmcnay.github.io/pandabook/) project amongst others.

## User Guide

Charts have mostly been built using [Plotly](https://plot.ly/python/) and are stored as HTML files. By default Plotly stores all the javascript required to render the plot in HTML (~3mb) which causes some serious bloating in project size, so most charts here are stored ex. JS.

To save a Plotly chart like this we need to set "include_plotlyjs" to 'cdn'

```
py.plot(fig, filename='savename.html', include_plotlyjs='cdn')
```

By using 'cdn' rather than False the output file includes an HTML tag that links to the .js externally. This means that the HTML files will render in a browser but *only if there is an internet connection* 

    <script src="https://cdn.plot.ly/plotly-latest.min.js"></script> 

For more information on this point look at the help file (online documentation is pretty poor)

```
help(plotly.offline.plot)
```