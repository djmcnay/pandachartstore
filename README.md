# pandachartstore

Chartstore is designed to be a dynamically updatable repo for charts used in the [Pontificating Panda Chartbook](https://djmcnay.github.io/pandabook/) project amongst others.

## User Guide


### Plotly
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

#### Rendering for Jupyter-Books
Thus far there appears to be two options, neither of which are ideal.

Firstly, we can take advantage of Jupyter magics and use HTML & object tags. In doing this we have to convert the Github repo into a github pages site and then link to the individual HTML page. **Hopefully** this provides a dynamic method, but that still needs testing. Very annoyingly the object tag needs height and width to be constructed manually 

```
%%html
<object data="https://djmcnay.github.io/pandachartstore/PlotlyHTMLexJS/pokemon.html" width="800", height="200"></object>
```

We can create equivalent code in Python either directly or using a lambda function

```
HTML('''<object data="https://djmcnay.github.io/pandachartstore/PlotlyHTMLexJS/pokemon.html" 
                width="800" height="500"></object>''')
                
ho= lambda l,w,h: HTML(str('<object data=\"https://djmcnay.github.io/pandachartstore/'+l
                           +'\" width=\"'+str(w)+'\" height=\"'+str(h)+'\"</object>'))
```

The other option is to read in the HTML file and use IPython.display. In this case we use the *raw* files from githubusercontent to read in the HTML, convert it from 'bytes' to 'string' and then display the HTML; this looks better but means the content is read in when the book is built (and is therefore static).

```
from IPython.display import display, HTML
from urllib.request import urlopen

link = "https://raw.githubusercontent.com/djmcnay/pandachartstore/master/PlotlyHTMLexJS/pokemon.html"
display(HTML(urlopen(link).read().decode("utf-8")))
```
