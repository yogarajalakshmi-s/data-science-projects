# Popular Languages

Analysis on popular programming languages since 2008, taking data from StackOverflow and deciding popularity based on number of times the languages were used as tags in a StackOverflow question.

**1. Data from StackOverflow**
  - Taken data from StackOverflow (https://data.stackexchange.com/stackoverflow/query/675441/popular-programming-languages-per-over-time-eversql-com) by executing this SQL query.
  ```
  select dateadd(month, datediff(month, 0, q.CreationDate), 0) m, TagName, count(*)
  from PostTags pt
  join Posts q on q.Id=pt.PostId
  join Tags t on t.Id=pt.TagId
  where TagName in ('java','c','c++','python','c#','javascript','assembly','php','perl','ruby','visual basic','swift','r','object-c','scratch','go','swift','delphi')
  and q.CreationDate < dateadd(month, datediff(month, 0, getdate()), 0)
  group by dateadd(month, datediff(month, 0, q.CreationDate), 0), TagName
  order by dateadd(month, datediff(month, 0, q.CreationDate), 0)
  ```
  - Deciding the popularity based on number of tags for each languages every year

**2. Read and clean data**
  - Read data from csv
  - Find the number of tags for each programming language.

**3. Data Manipulation**
  - Changing the data for better readability. (Date as row, Language as column and No. of tags as the values)

**4. Data Visualisaton with Matplotlib**
  - Creating a chart to visualise the popularity of each language from 2008 to 2023.
  - Row: Date, Column: No.of tags, Graph: Language
