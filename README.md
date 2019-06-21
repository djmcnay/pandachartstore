# pandachartstore

Chartstore is designed to be a dynamically updatable repo for charts used in the [Pontificating Panda Chartbook](https://djmcnay.github.io/pandabook/) project amongst others.

## User Guide

Most plots have been built using [Plotly](https://plot.ly/python/) and stored as HTML files. By default Plotly stores all the javascript required to render the plot in HTML but this can lead to some serious bloating in file size so most charts here are stored exJS.

To save a Plotly chart like this we need to set "include_plotlyjs" to False
```
py.plot(fig, filename='savename.html', auto_open=False, include_plotlyjs=False)
```

Rendering these later requires some additional HTML

<table>
    <tr>
        <td>Foo</td>
    </tr>
</table>



    <section>
      <p>example</p>
      <pre><code data-trim>
        <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
      </code></pre>
    </section>