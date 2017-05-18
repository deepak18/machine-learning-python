
# Fire up GraphLab Create

We always start with this line before using any part of GraphLab Create. It can take up to 30 seconds to load the GraphLab library - be patient!

The first time you use GraphLab create, you must enter a product key to license the software for non-commerical academic use. To register for a free one-year academic license and obtain your key, go to [dato.com](https://dato.com/download/academic.html).


```python
graphlab.get_dependencies()
```


```python
# import graphlab
# Set product key on this computer. After running this cell, you will not need to re-enter your product key. 
graphlab.product_key.set_product_key('YOUR_PRODUCT_KEY')

# Limit number of worker processes. This preserves system memory, which prevents hosted notebooks from crashing.
graphlab.set_runtime_config('GRAPHLAB_DEFAULT_NUM_PYLAMBDA_WORKERS', 4)

```

# Load a tabular data set


```python
sf = graphlab.SFrame('people-example.csv')
```




<pre>Parsing completed. Parsed 7 lines in 0.04311 secs.</pre>


    ------------------------------------------------------
    Inferred types from first 100 line(s) of file as 
    column_type_hints=[str,str,str,long]
    If parsing fails due to incorrect types, you can correct
    the inferred type list above and pass it to read_csv in
    the column_type_hints argument
    ------------------------------------------------------
    



<pre>Parsing completed. Parsed 7 lines in 0.01905 secs.</pre>


# SFrame basics


```python
sf # we can view first few lines of table
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">First Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Last Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Country</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">age</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Smith</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">24</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Williams</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Canada</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Jone</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">England</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Brown</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">USA</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Cooper</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Poland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Campbell</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Ward</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Switzerland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">25</td>
    </tr>
</table>
[7 rows x 4 columns]<br/>
</div>




```python
sf.tail()  # view end of the table
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">First Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Last Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Country</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">age</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Smith</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">24</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Williams</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Canada</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Jone</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">England</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Brown</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">USA</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Cooper</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Poland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Campbell</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Ward</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Switzerland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">25</td>
    </tr>
</table>
[7 rows x 4 columns]<br/>
</div>



# GraphLab Canvas


```python
# .show() visualizes any data structure in GraphLab Create
# If you want Canvas visualization to show up on this notebook, 
# add this line:
graphlab.canvas.set_target('ipynb')
```


```python
sf['age'].show(view='Categorical')
```



# Inspect columns of dataset


```python
sf['Country']
```




    dtype: str
    Rows: 7
    ['United States', 'Canada', 'England', 'USA', 'Poland', 'United States', 'Switzerland']




```python
sf['age']
```




    dtype: int
    Rows: 7
    [24L, 23L, 22L, 23L, 23L, 22L, 25L]



Some simple columnar operations


```python
sf['age'].mean()
```




    23.142857142857146




```python
sf['age'].max()
```




    25L



# Create new columns in our SFrame


```python
sf
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">First Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Last Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Country</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">age</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Smith</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">24</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Williams</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Canada</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Jone</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">England</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Brown</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">USA</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Cooper</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Poland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Campbell</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Ward</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Switzerland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">25</td>
    </tr>
</table>
[7 rows x 4 columns]<br/>
</div>




```python
sf['Full Name'] = sf['First Name'] + ' ' + sf['Last Name']
```


```python
sf
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">First Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Last Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Country</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">age</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Full Name</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Smith</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">24</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob Smith</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Williams</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Canada</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice Williams</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Jone</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">England</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm Jone</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Brown</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">USA</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix Brown</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Cooper</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Poland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex Cooper</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Campbell</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod Campbell</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Ward</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Switzerland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">25</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek Ward</td>
    </tr>
</table>
[7 rows x 5 columns]<br/>
</div>




```python
sf['age'] * sf['age']
```




    dtype: int
    Rows: 7
    [576L, 529L, 484L, 529L, 529L, 484L, 625L]



# Use the apply function to do a advance transformation of our data


```python
sf['Country']
```




    dtype: str
    Rows: 7
    ['United States', 'Canada', 'England', 'USA', 'Poland', 'United States', 'Switzerland']




```python
sf['Country'].show()
```




```python
def transform_country(country):
    if country == 'USA':
        return 'United States'
    else:
        return country
```


```python
transform_country('Brazil')
```




    'Brazil'




```python
transform_country('Brasil')
```




    'Brasil'




```python
transform_country('USA')
```




    'United States'




```python
sf['Country'].apply(transform_country)
```




    dtype: str
    Rows: 7
    ['United States', 'Canada', 'England', 'United States', 'Poland', 'United States', 'Switzerland']




```python
sf['Country'] = sf['Country'].apply(transform_country)
```


```python
sf
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">First Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Last Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Country</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">age</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Full Name</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Smith</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">24</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob Smith</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Williams</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Canada</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice Williams</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Jone</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">England</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm Jone</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Brown</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix Brown</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Cooper</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Poland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex Cooper</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Campbell</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod Campbell</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Ward</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Switzerland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">25</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek Ward</td>
    </tr>
</table>
[7 rows x 5 columns]<br/>
</div>
