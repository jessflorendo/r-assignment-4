

```python
import pandas as pd
import matplotlib.pyplot as plt
```


```python
#a fun thing I learned working on this assignment is that if you do print(4^1) in python you get 5. that's just not math
def num_kmers(sequence, k):
    """
    Summary: count number of kmers in given sequence
    This is (1) on the assignments requirements. Yields number of kmers only with given parameters.
    
    Parameters:
    sequence - string: line of DNA sequence --> specified with quotes 
    k - integer: length of substring
    """
    if k == 1:
        count = 4
    else:
        count = len(sequence) - k + 1 
    return count
```


```python
num_kmers("ATGC", 2)
```




    3




```python
def kmer_df(sequence):
    """
    Summary: construct a dataframe relating k value to kmers
    This is (2) on the assignments requirements. Uses panda to construct a dataframe.
    
    Parameters:
    sequence - string: line of DNA sequence
    """
    total = len(sequence)
    x_axis = range(1, total+1)
    y_axis = []
    for i in range(1,total+1):
        b = num_kmers(sequence, i)
        y_axis.append(b)
    data = {'k':x_axis, 'kmer':y_axis}
    df = pd.DataFrame(data)
    return df
```


```python
kmer_df("ATTGCCATGC")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>k</th>
      <th>kmer</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>9</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>8</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>7</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>6</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>5</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7</td>
      <td>4</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8</td>
      <td>3</td>
    </tr>
    <tr>
      <th>8</th>
      <td>9</td>
      <td>2</td>
    </tr>
    <tr>
      <th>9</th>
      <td>10</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
def kmer_graph(sequence):
    """
    Summary: construct a graph relating k value to kmers
    This is (3) on the assignments requirements. Uses panda to construct a dataframe and matplot to construct the plot.
    
    Parameters:
    sequence - string: line of DNA sequence
    """
    total = len(sequence)
    x_axis = range(1, total+1)
    y_axis = []
    for i in range(1,total+1):
        b = num_kmers(sequence, i)
        y_axis.append(b)
    data = {'k':x_axis, 'kmer':y_axis}
    dframe = pd.DataFrame(data)
    dframe.plot(kind = 'line', x = 'k', y = 'kmer')
    plot = plt.show()
    return plot
```


```python
kmer_graph("ATTGCCATGC")
```


![png](output_6_0.png)



```python
def kmer_lg(sequence, observed):
    """
    Summary: determine the linguistic complexity of the kmers
    This is (4) on the assignments requirements. Requires a given observed value.
    
    Parameters:
    sequence - string: line of DNA sequence
    observed - integer: given observed kmer occurence
    """
    total = len(sequence)
    y_axis = []
    for i in range(1,total+1):
        b = num_kmers(sequence, i)
        y_axis.append(b)
    sum = 0
    for num in y_axis:
        sum = sum +num
    result = observed/sum
    return result
```


```python
kmer_lg("ATTGCCATGC", 45)
```




    0.9183673469387755



The next part called for writing a script to thoroughly test each of these parts. I did this on my local hard drive through the bash/shell command line stuff we worked on at the beginning of the semester, but couldn't figure out how to share these results with you as they are basically modified rewrites of everything above. This is my evidence that I executed (5) at 1:20 AM. 


```python
def kmer(sequence, observed):
    total = len(sequence)
    x_axis = range(1, total+1)
    y_axis = []
    for i in range(1,total+1):
        b = num_kmers(sequence, i)
        y_axis.append(b)
    data = {'k':x_axis, 'kmer':y_axis}
    df = pd.DataFrame(data)
    df.plot(kind = 'line', x = 'k', y = 'kmer')
    plot = plt.show()
    sum = 0
    for num in y_axis:
        sum = sum +num
    result = observed/sum
    final = "use print() with df or result to see dataframe and linguistic complexity"
    #I couldn't figure out how to display graph, lg, and dataframe all as output of command
    #at least this way the results explain how to do that?
    return final
```
