
# Hello everyone ! 

Welcome to your first exericse in data science. Many of you will be relatively new to data analytic statistical programming and modeling environments so we will use iPython notebook as an easy interactive interface into Python27. Specifically, we will be using numpy and it's related (and much cleaned up) dependency, Pandas. Together, with matplotlib, these modules makes Python into a powerful analysis tool. 

We will start our first journey into data science by covering the basics of summary statistics. 


```python
# For those of you who are familiar with other programming languages, import is similar to "library" in C++ or R.  In truth, 
# anything can be done using just the base data/variable types and methods for Python... assuming you have enough time to figure
# out and develop the code yourself. However Time = $, and so you'll find knowing key libraries such as numpy, pandas, and scikit
# -learn will greatly increase your ability to timely deliver penetrating analysis with minnimal pain. 

import sys
import numpy as np  # the as reserved word is part of aliasing, mostly for aeshtetic purposes
import pandas as pd
import matplotlib.pyplot as plt
```

# Sec 1.1 Loading up your data and basic exploration

The first step of any data analysis is to load up your data. Since we're here to make you into an honest-to-goodness data scientist, and not an academic, it will be most instructive to utilize a real data set that's been used for actual data analysis by a company or government. 

For this first exercise, we'll be using the Cooperative Research (CORE) data. CORE was constructed through a grant from the  National Science Foundation (NSF), and is taken from firm filings with the Federal Registrar. It's been used in many different contexts, including assessing possibe monpolies by the Dept. of Justice Anti-Trust Division, to network theorists studying firm-based research networks in the United States in academia. 

We'll load up just the base version of the data from 2005.  It includes the year of filing for creating the joint research consortium to the registrar, the number of members in said consortium, as well as variables indicating the major sectors the consortium planns to operate in. 

Conveniently, this data set has each 'type' of variables present (please reference previous lecture on data types). For today's exercise we'll start our investigation with the numeric type, or the number of members in in the joint research consortium. 


```python
CORE_dat = pd.read_csv('C:/Users/Amadeus/Desktop/CORE Data/2006 CORE database.csv')
print(type(CORE_dat))
CORE_dat.head(10)
```

    <class 'pandas.core.frame.DataFrame'>
    




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>RECNO</th>
      <th>YEAR</th>
      <th>FEDREGDATE</th>
      <th>NAME</th>
      <th>TECH</th>
      <th>NUMMEMB</th>
      <th>FEDLAB</th>
      <th>DOD</th>
      <th>DOE</th>
      <th>NASA</th>
      <th>...</th>
      <th>Unnamed: 65</th>
      <th>Unnamed: 66</th>
      <th>Unnamed: 67</th>
      <th>Unnamed: 68</th>
      <th>Unnamed: 69</th>
      <th>Unnamed: 70</th>
      <th>Unnamed: 71</th>
      <th>Unnamed: 72</th>
      <th>Unnamed: 73</th>
      <th>Unnamed: 74</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1985</td>
      <td>01/17/85</td>
      <td>Software Productivity Consortium ('SPC')</td>
      <td>sof</td>
      <td>22</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>1985</td>
      <td>01/17/85</td>
      <td>Microelectronics and Computer Technology Corp....</td>
      <td>sub</td>
      <td>70</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>1985</td>
      <td>01/17/85</td>
      <td>Exxon Production Research Co.</td>
      <td>enr</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>1985</td>
      <td>01/24/85</td>
      <td>Consortium for Advanced Manufacturing-Internat...</td>
      <td>aut</td>
      <td>89</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>1985</td>
      <td>01/30/85</td>
      <td>Bellcore</td>
      <td>tel</td>
      <td>9</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>1985</td>
      <td>01/30/85</td>
      <td>Semiconductor Research Corp. (SRC)</td>
      <td>sub</td>
      <td>40</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>1985</td>
      <td>01/31/85</td>
      <td>Bethlehem/US Steel</td>
      <td>man</td>
      <td>5</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>1985</td>
      <td>02/01/85</td>
      <td>Center for Advanced Television Studies</td>
      <td>tel</td>
      <td>9</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>10</td>
      <td>1985</td>
      <td>02/04/85</td>
      <td>Medium Range Truck Transmission Cooperative Pr...</td>
      <td>trn</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>10 rows × 75 columns</p>
</div>



Notice that the data has a few 'NaN' (namely the first row and a bunch on the right). NaN stands for Not-a-Number, and can be the bain of your existence when numerous. Often, if you pass a column of data with NaN values present to a numerical procedure or algorithm, you will get a traceback error. Some methods have explicit 'controls' that automatically ignores NaNs, otherwise, you will have to remove them yourself. 

In general, removing NaNs, NAs, or missing value are not a trivial matter. In particular, we could break down missing data into 3 broad cases: 

1. Data missing completely at random
2. Data missing at random
3. Data missing not at random 

As we start to build models, and engage in preprocessing, we will revisit this topic and go into depth on how to deal with each case. 

It is possible to deal with the missing data in a wide spectrum of ways, from simply replacing values with 0, or the average, if it's a numeric column; to deploying procedures like K-Nearest Neighbors to impute missing values. For now, we'll assume data is missing completely at random, and thus remove the NaNs by dropping them from the column of interest. 


```python
# There are several ways to remove NaNs. Because we used read_csv to read in our csv file into our Python environment, our data 
# is housed in a Pandas Data Frame. For those of you familiar with R, Panda's data frame operates very much like the R data frame
# in that it allows for mixed type data to enter into one object, the data frame. 

# A further benefit of being in a Panda's data frame is that we can call Pandas data frame methods by invoking the '.' operator. 
# It just so happens there is a simple method to remove NAs. 

CORE_dat1 = CORE_dat.dropna(how = 'all')

# Since we're goign to deal specifically with summary statistics on numerical data , let's isolate this one column for further 
# analysis. Note, instead of directly mutating, changing my data frame, each alteration is it's own copy. Not highly recommended
# if you have a lot of data as each copy will take up space as cache in memory or drive space, but an effective as we start out, 
# so we can easily trace back to a previous 'version' of our data if we make mistakes in the future. 

Nummemb = CORE_dat1['NUMMEMB']

Nummemb.dtype
```




    dtype('O')



Uh oh, this is a problem. Notice I typed 'Nummemb.dtype' into our code prompt, and it outputted 'dtype('0')'. However, Nummemb should be numeric, and without Python recognizing this data as numeric, we will not be able to do numeric operation on the data. Have no fear! Luckily, the Pandas environment has a clear and easy solution to this dilemma via the function 'to_numeric'. 


```python
#Note - we call all pandas function by prefacing the function withi a 'pd.' Computer Scientists have chosen this convention to 
# avoid 'collisions in namespaces', but since we're data scientists, we can safetly ignore all that mumbo jumbo and be blissfully
# unawares!

Nummemb_Numeric = pd.to_numeric(Nummemb, errors='coerce')
Nummemb_Numeric.dtype
```




    dtype('float64')



Something to think about: Interesting, why did Python coerce the above numeric into a float and not an integer? Does it matter? 

Finally, we're now ready to do some summary statistics on our numeric data! 

# Section 1.2 - Summary Statistics 


```python
from IPython.display import Image
Image(url='http://media.buzzle.com/media/images-en/gallery/quotes/funny/450-chinese-proverb-work.jpg')

```




<img src="http://media.buzzle.com/media/images-en/gallery/quotes/funny/450-chinese-proverb-work.jpg"/>



"The Analysis Script of a thousand lines starts with the summary statistics" - Chris The Data Scientist (circa. 2015)

I'm not sure if the above version of the ancient Lao Tzu wisdom is any more or less profound, but it is just as accurate. As you grow in your data science career, you will deploy all kinds of crazy sounding algorithms and probably have to cycle through thousands of computations. Yet, it all has to start with getting a basic grasp of your data, and no better way to get a good grasp of your data by calculating some "population parameters" (We'll refer to them as PPs from here-on-in). 

So what are PPs? Data Science is not magic, although it may seem like it to the laymen. When a data scientist (or her more serious, less fun, academic counterpart the statistcian) aserts some far-reaching conclusion about something, they are engaging in something called 'inference'. 

Now there are several types of inferences (Don't worry, we're only going to talk about 1), and the most important type you will have to master is statistical inference. 

What is that you may ask? Essentially, it's making inferences from limited information. More precisely, it's infering things about your "population parameters" from sample statistics. 

Now, at some point, back in the days of yore (circa. the 1800s), some French mathematician discovered all kinds of formal theories about chance, and how to understand chance events. Since this frenchmen was a mathematician however, instead of understanding chance through rhetoric like a philosopher, or experimentation like a scientist, he decided to build a abstract model.

Since we're not mathematicians, we won't go too much into detail about these models (yet). All you need to know is that this frenchmen's model had a few ingredients. One was the probability distribution, and one of the other components were the PPs. This frenchmen also made his theory into a sort of game, with the goal being to "infer" as much as possible about the "true" population and it's parameters through observing the samples. 

What are intelligent ways we can observe samples? Let's find out below.

## 1.2.1 - Mode

What is the mode? Simply put, it's the element in your set that is most frequent in the set. So if we had a bag with 3 yellow balls, ,2 white balls, and 1 blue ball, the elemnts labeled "yellow" would be the mode. 

In our context, it's the value that most often appears in our Pandas numeric data column. Got it? Good. Code it up. 



```python
#Mode of a list, or series etc. 
# I'll provide some starter code and you complete it 
def my_mode(dat_column):
    if len(dat_column) == 0:
        return None
    max_curr = 0
    for num in dat_column:
        #Your code here
        pass
    return (max_curr)    

#Hint - we want to 
```

## 1.2.2 - Median 

Ok, now we can move on to something slightly more interesting, Median. The median is the element in the "exact middle" of the data column if we were to order all values from lowest to highest. But wait... what if there were even number of elements in our data column? You got me! Then we cheat and add the 2 values in the middle and divide by 2. 

This will be the first 'measure of centrality' we encounter. It's cousin, the mean, is more often use, but median has it's perks as well, including being 'more robust to changes in the data set. What kind of changes? Remember that issue of missing values that we mentioned above? How you impute missing values can greatly impact your mean. However, whatever those impacts are, they are less likely to impact the median as much. Therefore, median is seen as a more 'stable' sample parameter. 

Got it? Good. Code it. 


```python
def my_median(dat_column):
    dat_column_sort = []
    #Some code here probably
    if len(lst) < 1:
            return None
    if len(dat_column_sort)%2 == 1:
        pass #Your code here
    else:
        pass #Your code here
```

## 1.2.3 - Mean
Great. Now we're going to go onto the big kahunna of PPs, the mean. Although, this one has many names, the average, the expected value, the first moment, etc. Even if you haven't used it that often you probably know what it is, the average is just adding all the values in our data column together and dividing by the number of elements in the data column. 

Easy right? Code it up! 

```python
def my_mean(dat_column):
    the_average = 0
    sum_of_column = 0
    length_of_column = len(dat_column)
    for num in dat_column:
        #Your code here 
        pass
    return None # Change None to your value after you write your code
```

## 1.2.4 - Max/Min

We saved the easiest to describe PP for last and we'll combine both parameters into one function. This will be slightly trickier than the above, as you'll have to return a list that contains both max and min. 

What is the max? It's just the maximum value of your data column. Likewise, the min is the minnimum value of your data column. Too simple? Prove it. Code it up. 


```python
# We'll let you cheat on this one, you can invoke Python's sort method to make this easier

def my_max_and_min(dat_column):
    sorted_column = []
    min = 0; max = 0;
    two_tuple_list = []
    pass # Write code here
    return None # Change this to return two_tuple_list with your max and min
```


```python

```

# Sec 1.3 - Computing Effeciency (or why Elaine is right, and computing PPs with the right pipes really matters for data scientist)


```python
from IPython.display import Image
Image(url='http://i.imgur.com/dgCehHE.jpg')
```




<img src="http://i.imgur.com/dgCehHE.jpg"/>



Got some coding done. Feeling good? Great! So now you can write methods that can compute the standard 4 PPs for your sample of data. So whenever you have a problem, you'll be confident enough to just write up your own method and execute right? Well... not exactly. 

Although the methods you wrote above were accurate, and got the job done. As data scientists, we'll eventually deal with REALLY large data, and work with REALLY complicated algorithms and procedures. When all these complexities get thrown in our way, the effeciency of the algorithm/methods will start to matter. Later on in our journey, we'll deal with something called run-time and Big Oh (not the anime character) for algorithmetic complexity. 

In general, we want to use "effecient" code pipes to calculate our PPs (and any other computation). Therefore, we'll want to use pre-built methods as much as possible IF we know those methods were well coded. What is well coded/designed for our purposes? We can assume that most of Pandas, Numpy, and any other major library falls under that category for now. How are these pipes more effeceint? In many cases the pipes were probably written partially in C++ (remember having to install Cython in the first day? Cython = C++ & Python). In other cases, the procedures were probably written "more" cleverly than we hacked out above. 

Don't fret however, with enough practice, you too will be able to write extremely effecient code. In the mean time, check out the below Pandas methods for the PPs. 


```python
Nummemb_Numeric.mode()
```




    0    2
    dtype: float64




```python
Nummemb_Numeric.median()
```




    5.0




```python
Nummemb_Numeric.max()
```




    539.0




```python
Nummemb_Numeric.min()
```




    1.0




```python
Nummemb_Numeric.mean()
```




    13.237006237006238



Want to compare the run-time of Pandas methods with yours? try the below:


```python
import timeit
start = timeit.default_timer()
# put either your function or the pandas methods in here and you can see how long it takes the computer to calculate. 
stop = timeit.default_timer()
```

# For next time

Please make sure you understand the 4 PPs, and how they can be used to describe a sample. We will discuss variance and standard deviation next week, as well as begin more complicated topics of statistical inference, including convergence of distributions in the more theoretical leg, and hypothesis testing in the more practical one. 


```python

```
