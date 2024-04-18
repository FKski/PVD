## Ptyhon

#### Read csv into df(default sep=',')
df = pd.read_csv('universities.csv')
df = pd.read_csv('cities-in-poland.csv', sep=';')

#### Display options
pd.set_option('display.max_rows', 10)

#### Display descriptive statistics for income earned.
df.describe()
series.describe()

---
### Creating Data Frame

#### Creating DataFrame with column names
company = pd.DataFrame(data=company_data, columns=['Month','Income'])

---
### Selections

#### Selection based on row/column names
df.loc[row,column]
df.loc[:,not('Movie')]
df.loc[:,['Total', 'Name']]

#### Selection based on row/column numbers
df.iloc[[10,3,17],[2,3]]

#### Fist/last rows of data (default 5)
oscars.head()
oscars.tail()

---
### Save to file

#### Saved to csv file
movies.to_csv('movies.csv', index=True)
df.loc[:,['salary', 'sex', 'country']].groupby(['country', 'sex']).median().to_csv('wyniki.csv')

#### Saved to html (table)
moviesHtml.to_html('moviesHtml.html',index=False)

---
### Change indexes
tests.index = ['John Brown','Sarah Green','Peter Black']

---
### Adding cols

#### Make new column
df['a+b'] = df['a'] + df['b']
df['Over limit'] = np.where(df['Over limit'] < 0, 0, df['Over limit'])

---
### Sorting

#### Sorting values (default ascending=True)
df.sort_values(by='Name', ascending=False)
df.sort_values(by=['Result', 'Total'], ascending=False)
df.sort_values(by=['Result', 'Total', 'Name'], ascending=[False,False,True])

#### Sort then show first 10 rows
df.sort_values(by='City')[:10]

---
### Queries

#### Queries (column where city is krakow)
df.query("City=='Krakow'")

#### Queries (column where city is krakow and Students >= 10000)
df.query("City=='Krakow' and Students >= 10000")

#### Queries (with or)
df.query("movie_title == 'Avatar' or movie_title == 'Nomadland'")

---
### Grouping

#### Grouping (sum of visits, grouped by day)
df.loc[:,['Day','Visits']].groupby(['Day']).sum()

#### Grouping (mean of visits, grouped by days THEN browser)
df.loc[:,['Day','Visits','Browser']].groupby(['Day','Browser']).mean()

#### Grouping (count browsers by days)
visits.loc[:,['Day','Browser']].groupby(['Day']).count()

#### Grouping (count amount of male/female, store in new column)
df['sex_count'] = 0
df.loc[:,['sex', 'sex_count']].groupby('sex').count()

#### Grouping (median of salary)
df.loc[:,['salary', 'sex', 'country']].groupby(['country', 'sex']).median()

---
### Print mean of values in specific column
df['age'].mean()

---
### Data Joining (https://realpython.com/pandas-merge-join-and-concat/)
df= pd.merge(df1, df2, on='FIELD_NAME')
orders_wit_discounts = pd.merge(orders_with_prices, discounts, on='Product')

---
### Plots

#### Print plot
ds = pd.Series(data)
ds.plot()

#### Add labels on x axis
ds.index = ['Monday','Tuesday','Wednesday','Thursday','Friday']

#### Add title of the plot
ds.plot(title="People Watched a Movie")

#### Add x axis description
ds.plot(title="People Watched a Movie", xlabel='Days of Week')

#### Change plot type
ds.plot(kind='bar')

#### Pie bar with rounding to single digit
ds.plot(kind='pie', autopct='%1.0f%%')

---
## EXCEL

#### To create a table, select data and press CTRL+L
#### To add sum row, go to Projekt Tabeli tab and select Wiersz Sumy

### Pivot table
#### To create pivot table (tabela przestawna) go to Wstawianie and choose Tabela przestawna

### Power Query
#### Dane > pobierz dane > z pliku > (utf-8,separator,)
#### Przekształć dane (typ,usuń kolumne, dodaj kolumne)