
# Fire up GraphLab Create


```python
import graphlab
import graphlab.aggregate as agg
```

# Load some house sales data


```python
sales = graphlab.SFrame('home_data.gl/')
```


```python
sales
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">id</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">date</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">price</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">bedrooms</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">bathrooms</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_living</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_lot</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">floors</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">waterfront</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7129300520</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014-10-13 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">221900</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1180</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5650</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">6414100192</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014-12-09 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">538000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2.25</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2570</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7242</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5631500400</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2015-02-25 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">180000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">770</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">10000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2487200875</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014-12-09 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">604000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1960</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1954400510</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2015-02-18 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">510000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1680</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8080</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7237550310</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014-05-12 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1225000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4.5</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5420</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">101930</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1321400060</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014-06-27 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">257500</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2.25</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1715</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">6819</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2008000270</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2015-01-15 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">291850</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1.5</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1060</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">9711</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2414600126</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2015-04-15 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">229500</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1780</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7470</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3793500160</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2015-03-12 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">323000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2.5</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1890</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">6560</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
</table>
<table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">view</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">condition</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">grade</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_above</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_basement</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">yr_built</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">yr_renovated</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">zipcode</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">lat</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1180</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1955</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98178</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.51123398</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2170</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">400</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1951</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1991</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98125</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.72102274</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">6</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">770</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1933</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98028</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.73792661</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1050</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">910</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1965</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98136</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.52082</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1680</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1987</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98074</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.61681228</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">11</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3890</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1530</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2001</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98053</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.65611835</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1715</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1995</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98003</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.30972002</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1060</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1963</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98198</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.40949984</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1050</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">730</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1960</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98146</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.51229381</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1890</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2003</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98038</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.36840673</td>
    </tr>
</table>
<table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">long</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_living15</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_lot15</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.25677536</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1340.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5650.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.3188624</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1690.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7639.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.23319601</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2720.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8062.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.39318505</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1360.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5000.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.04490059</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1800.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7503.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.00528655</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4760.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">101930.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.32704857</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2238.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">6819.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.31457273</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1650.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">9711.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.33659507</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1780.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8113.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.0308176</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2390.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7570.0</td>
    </tr>
</table>
[21613 rows x 21 columns]<br/>Note: Only the head of the SFrame is printed.<br/>You can use print_rows(num_rows=m, num_columns=n) to print more rows and columns.
</div>



# Exploring data for housing sales


```python
graphlab.canvas.set_target('ipynb')
sales.show(view = "Scatter Plot", x="sqft_living", y="price")
```



# Create a simple regression model of sqft_living to price


```python
train_data,test_data = sales.random_split(.8, seed=0)
```

# Build the regression model


```python
sqft_model = graphlab.linear_regression.create(train_data, target='price', features=['sqft_living'])
```

    PROGRESS: Creating a validation set from 5 percent of training data. This may take a while.
              You can set ``validation_set=None`` to disable validation tracking.
    
    


<pre>Linear regression:</pre>



<pre>--------------------------------------------------------</pre>



<pre>Number of examples          : 16508</pre>



<pre>Number of features          : 1</pre>



<pre>Number of unpacked features : 1</pre>



<pre>Number of coefficients    : 2</pre>



<pre>Starting Newton Method</pre>



<pre>--------------------------------------------------------</pre>



<pre>+-----------+----------+--------------+--------------------+----------------------+---------------+-----------------+</pre>



<pre>| Iteration | Passes   | Elapsed Time | Training-max_error | Validation-max_error | Training-rmse | Validation-rmse |</pre>



<pre>+-----------+----------+--------------+--------------------+----------------------+---------------+-----------------+</pre>



<pre>| 1         | 2        | 1.005147     | 4350281.148463     | 2246638.464824       | 263020.285748 | 261497.543973   |</pre>



<pre>+-----------+----------+--------------+--------------------+----------------------+---------------+-----------------+</pre>



<pre>SUCCESS: Optimal solution found.</pre>



<pre></pre>


# Evaluate the simple model


```python
print test_data['price'].mean()
```

    543054.042563
    


```python
print sqft_model.evaluate(test_data)
```

    {'max_error': 4144088.343371106, 'rmse': 255184.85316374677}
    

# Let's show what our predictions look like


```python
import matplotlib.pyplot as plt
%matplotlib inline
```


```python
plt.plot(test_data['sqft_living'], test_data['price'], '.',
        test_data['sqft_living'],sqft_model.predict(test_data), '-')
```




    [<matplotlib.lines.Line2D at 0x1f0e6198>,
     <matplotlib.lines.Line2D at 0x1f0e6240>]




![png](output_16_1.png)



```python
sqft_model.get('coefficients')
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">index</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">value</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">stderr</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">(intercept)</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-46636.101539</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5054.00343049</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">sqft_living</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">281.855182828</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2.22196715615</td>
    </tr>
</table>
[2 rows x 4 columns]<br/>
</div>



# Explore other features in the data


```python
my_features = ['bedrooms', 'bathrooms', 'sqft_living', 'sqft_lot', 'floors', 'zipcode']
```


```python
sales[my_features].show()
```




```python
sales.show(view="BoxWhisker Plot", x="zipcode", y="price")
```



# Build a regression model with more features


```python
my_features_model = graphlab.linear_regression.create(train_data, target='price', features=my_features, validation_set=None)
```


<pre>Linear regression:</pre>



<pre>--------------------------------------------------------</pre>



<pre>Number of examples          : 17384</pre>



<pre>Number of features          : 6</pre>



<pre>Number of unpacked features : 6</pre>



<pre>Number of coefficients    : 115</pre>



<pre>Starting Newton Method</pre>



<pre>--------------------------------------------------------</pre>



<pre>+-----------+----------+--------------+--------------------+---------------+</pre>



<pre>| Iteration | Passes   | Elapsed Time | Training-max_error | Training-rmse |</pre>



<pre>+-----------+----------+--------------+--------------------+---------------+</pre>



<pre>| 1         | 2        | 0.024566     | 3763208.270523     | 181908.848367 |</pre>



<pre>+-----------+----------+--------------+--------------------+---------------+</pre>



<pre>SUCCESS: Optimal solution found.</pre>



<pre></pre>



```python
print sqft_model.evaluate(test_data)
print my_features_model.evaluate(test_data)
```

    {'max_error': 4144088.343371106, 'rmse': 255184.85316374677}
    {'max_error': 3486584.509381705, 'rmse': 179542.4333126903}
    

# Apply learned models to predict prices of 3 houses

## House 1


```python
house1 = sales[sales['id'] == '5309101200']
```


```python
house1
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">id</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">date</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">price</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">bedrooms</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">bathrooms</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_living</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_lot</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">floors</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">waterfront</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5309101200</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014-06-05 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">620000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2.25</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2400</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5350</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1.5</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
</table>
<table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">view</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">condition</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">grade</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_above</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_basement</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">yr_built</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">yr_renovated</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">zipcode</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">lat</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1460</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">940</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1929</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98117</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.67632376</td>
    </tr>
</table>
<table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">long</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_living15</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_lot15</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.37010126</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1250.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4880.0</td>
    </tr>
</table>
[? rows x 21 columns]<br/>Note: Only the head of the SFrame is printed. This SFrame is lazily evaluated.<br/>You can use sf.materialize() to force materialization.
</div>



<img src="house-5309101200.jpg">


```python
house1['price']
```




    dtype: int
    Rows: ?
    [620000L, ... ]




```python
print sqft_model.predict(house1)
```

    [629816.3372479538]
    


```python
print my_features_model.predict(house1)
```

    [721918.9333272863]
    

## House 2


```python
house2 = sales[sales['id']=='1925069082']
```


```python
house2
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">id</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">date</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">price</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">bedrooms</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">bathrooms</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_living</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_lot</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">floors</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">waterfront</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1925069082</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2015-05-11 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2200000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4.25</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4640</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22703</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
    </tr>
</table>
<table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">view</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">condition</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">grade</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_above</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_basement</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">yr_built</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">yr_renovated</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">zipcode</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">lat</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2860</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1780</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98052</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.63925783</td>
    </tr>
</table>
<table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">long</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_living15</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_lot15</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.09722322</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3140.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">14200.0</td>
    </tr>
</table>
[? rows x 21 columns]<br/>Note: Only the head of the SFrame is printed. This SFrame is lazily evaluated.<br/>You can use sf.materialize() to force materialization.
</div>




```python
print sqft_model.predict(house2)
```

    [1261171.9467824404]
    


```python
print my_features_model.predict(house2)
```

    [1446472.4690774973]
    

## House 3


```python
bill_gates_house =  {'bedrooms':[8], 
              'bathrooms':[25], 
              'sqft_living':[50000], 
              'sqft_lot':[225000],
              'floors':[4], 
              'zipcode':['98039'], 
              'condition':[10], 
              'grade':[10],
              'waterfront':[1],
              'view':[4],
              'sqft_above':[37500],
              'sqft_basement':[12500],
              'yr_built':[1994],
              'yr_renovated':[2010],
              'lat':[47.627606],
              'long':[-122.242054],
              'sqft_living15':[5000],
              'sqft_lot15':[40000]}
```

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/d9/Bill_gates%27_house.jpg/2560px-Bill_gates%27_house.jpg">


```python
print my_features_model.predict(graphlab.SFrame(bill_gates_house))
```

    [13749825.525719076]
    

# Assignment


```python
avgpriceByZip = sales.groupby(key_columns='zipcode', operations={'avgPrice' : agg.MEAN('price')}).sort('avgPrice',ascending = False)
```


```python
avgpriceByZip
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">zipcode</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">avgPrice</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98039</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2160606.6</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98004</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1355927.09779</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98040</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1194230.00355</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98112</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1095499.36803</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98102</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">901258.238095</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98109</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">879623.623853</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98105</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">862825.231441</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98006</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">859684.763052</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98119</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">849448.01087</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98005</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">810164.880952</td>
    </tr>
</table>
[70 rows x 2 columns]<br/>Note: Only the head of the SFrame is printed.<br/>You can use print_rows(num_rows=m, num_columns=n) to print more rows and columns.
</div>




```python
avgpriceByZip['avgPrice'].max()
```




    2160606.6




```python
heightAvgZip = avgpriceByZip['avgPrice' == (avgpriceByZip['avgPrice'].max())]['zipcode']
```


```python
heightAvgZip
```




    '98039'




```python
sales.show(view="BoxWhisker Plot", x="zipcode", y="price")
```




```python
house_heighest_avg = sales[sales['zipcode'] == heightAvgZip]
```


```python
house_heighest_avg
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">id</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">date</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">price</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">bedrooms</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">bathrooms</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_living</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_lot</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">floors</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">waterfront</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3625049014</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014-08-29 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2950000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3.5</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4860</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23885</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2540700110</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2015-02-12 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1905000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3.5</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4210</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">18564</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3262300940</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014-11-07 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">875000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1220</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8119</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3262300940</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2015-02-10 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">940000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1220</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8119</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">6447300265</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014-10-14 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4000000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.5</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7080</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">16573</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2470100110</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014-08-04 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5570000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.75</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">9200</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">35069</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2210500019</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2015-03-24 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">937500</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1320</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8500</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">6447300345</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2015-04-06 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1160000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2680</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">15438</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">6447300225</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014-11-06 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1880000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2.75</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2620</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">17919</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2525049148</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014-10-07 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3418800</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5450</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">20412</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
</table>
<table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">view</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">condition</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">grade</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_above</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_basement</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">yr_built</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">yr_renovated</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">zipcode</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">lat</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">12</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4860</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1996</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98039</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.61717049</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">11</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4210</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2001</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98039</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.62060082</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1220</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1955</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98039</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.63281908</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1220</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1955</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98039</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.63281908</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">12</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5760</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1320</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2008</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98039</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.61512031</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">13</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">6200</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2001</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98039</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.62888314</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1320</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1954</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98039</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.61872888</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2680</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1902</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1956</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98039</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.61089438</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">9</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2620</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1949</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98039</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.61435052</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">11</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5450</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98039</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.62087993</td>
    </tr>
</table>
<table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">long</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_living15</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_lot15</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.23040939</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3580.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">16054.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.2245047</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3520.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">18564.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.23554392</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1910.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8119.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.23554392</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1910.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8119.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.22420058</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3140.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">15996.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.23346379</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3560.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">24345.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.22643371</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2790.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">10800.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.22582388</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4480.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">14406.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.22772057</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3400.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">14400.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.23726918</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3160.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">17825.0</td>
    </tr>
</table>
[? rows x 21 columns]<br/>Note: Only the head of the SFrame is printed. This SFrame is lazily evaluated.<br/>You can use sf.materialize() to force materialization.
</div>




```python
print house_heighest_avg['price'].mean()
```

    2160606.6
    


```python
house_range = sales[(sales['sqft_living'] > 2000) & (sales['sqft_living'] <=4000)]
```


```python
house_range
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">id</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">date</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">price</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">bedrooms</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">bathrooms</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_living</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_lot</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">floors</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">waterfront</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">6414100192</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014-12-09 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">538000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2.25</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2570</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7242</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1736800520</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2015-04-03 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">662500</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2.5</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3560</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">9796</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">9297300055</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2015-01-24 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">650000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2950</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2524049179</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014-08-26 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2000000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2.75</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3050</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">44867</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7137970340</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014-07-03 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">285000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2.5</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2270</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">6300</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3814700200</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014-11-20 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">329000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2.25</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2450</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">6500</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1794500383</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014-06-26 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">937000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1.75</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2450</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2691</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1873100390</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2015-03-02 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">719000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2.5</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2570</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7173</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8562750320</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014-11-10 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">580500</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2.5</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2320</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3980</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0461000390</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2014-06-24 00:00:00+00:00</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">687500</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1.75</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2330</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1.5</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
</table>
<table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">view</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">condition</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">grade</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_above</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_basement</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">yr_built</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">yr_renovated</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">zipcode</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">lat</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2170</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">400</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1951</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1991</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98125</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.72102274</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1860</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1700</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1965</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98007</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.60065993</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">9</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1980</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">970</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1979</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98126</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.57136955</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">9</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2330</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">720</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1968</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98040</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.53164379</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2270</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1995</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98092</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.32658071</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2450</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1985</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98030</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.37386303</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1750</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">700</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1915</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98119</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.63855772</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2570</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2005</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98052</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.70732168</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2320</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2003</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98027</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.5391103</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1510</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">820</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1929</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">98117</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">47.68228235</td>
    </tr>
</table>
<table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">long</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_living15</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sqft_lot15</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.3188624</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1690.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7639.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.14529566</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2210.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8925.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.37541218</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2140.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4000.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.23345881</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4110.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">20336.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.16892624</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2240.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7005.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.17228981</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2200.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">6865.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.35985573</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1760.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3573.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.11029785</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2630.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">6026.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.06971484</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2580.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3980.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-122.36760203</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1460.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5000.0</td>
    </tr>
</table>
[? rows x 21 columns]<br/>Note: Only the head of the SFrame is printed. This SFrame is lazily evaluated.<br/>You can use sf.materialize() to force materialization.
</div>




```python
frac_houses = house_range.num_rows() /  float(sales.num_rows())
```


```python
print frac_houses
```

    0.421875722945
    


```python
advanced_features = [
'bedrooms', 'bathrooms', 'sqft_living', 'sqft_lot', 'floors', 'zipcode',
'condition', # condition of house				
'grade', # measure of quality of construction				
'waterfront', # waterfront property				
'view', # type of view				
'sqft_above', # square feet above ground				
'sqft_basement', # square feet in basement				
'yr_built', # the year built				
'yr_renovated', # the year renovated				
'lat', 'long', # the lat-long of the parcel				
'sqft_living15', # average sq.ft. of 15 nearest neighbors 				
'sqft_lot15', # average lot size of 15 nearest neighbors 
]
```


```python
advanced_features_model = graphlab.linear_regression.create(train_data, target='price', features=advanced_features, validation_set=None)
```


<pre>Linear regression:</pre>



<pre>--------------------------------------------------------</pre>



<pre>Number of examples          : 17384</pre>



<pre>Number of features          : 18</pre>



<pre>Number of unpacked features : 18</pre>



<pre>Number of coefficients    : 127</pre>



<pre>Starting Newton Method</pre>



<pre>--------------------------------------------------------</pre>



<pre>+-----------+----------+--------------+--------------------+---------------+</pre>



<pre>| Iteration | Passes   | Elapsed Time | Training-max_error | Training-rmse |</pre>



<pre>+-----------+----------+--------------+--------------------+---------------+</pre>



<pre>| 1         | 2        | 0.032030     | 3469012.450686     | 154580.940736 |</pre>



<pre>+-----------+----------+--------------+--------------------+---------------+</pre>



<pre>SUCCESS: Optimal solution found.</pre>



<pre></pre>



```python
print my_features_model.evaluate(test_data)
print advanced_features_model.evaluate(test_data)
```

    {'max_error': 3462350.260179847, 'rmse': 179400.60890613243}
    {'max_error': 3556849.413858208, 'rmse': 156831.1168021901}
    


```python
rmse_diff = my_features_model.evaluate(test_data)['rmse'] - advanced_features_model.evaluate(test_data)['rmse']
```


```python
rmse_diff
```




    22569.49210394232




```python

```
