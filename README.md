# IMDB-Dataset-Pre-Processing

## Cleaning of IMDb TV Series Dataset

The project outlines a data cleaning workflow using the IMDb dataset which demonstrates various cleaning techniques and identifying use-cases for the cleaned dataset. This project demonstrates cleaning the datasets and implementing a few use cases. The softwares and the tools which were used to clean and organize the dataset are Python- Jupyter notebook, YesWorkFlow.

IMDB abbreviation for internet movie database is an online database used to retrieve information on films, television programs, video games, and streaming content also giving information on cast, production, biographies, plot summaries, trivia, ratings, critical reviews and other details. It is now a subsidiary of Amazon. As per recent statistics, IMDB has about 6.5 million titles including episodes and 10.4 million personalities in its database apart from 83 million users who are registered. IMDB recently launched IMDB TV which offers users to watch certain movies with advertisements but it is only limited to users in the USA. The datasets have been obtained from the official IMDb website. The purpose of the project is to clean multiple IMDB dataset and merge them into a single file. The analysis is done and the use cases are on the popularity of movies based on genre, popularity based on year of release, predict the rating of the movie based on various factors, popularity based on title and runtime of the movie, popular cast and their primary profession, number of adult vs non-adult movie and top 100 movies based on the rating.

### Dataset structure and content:
The IMDb dataset for this project has been initially divided into 7 different files where each
dataset is contained in a gzipped, tab-separated-values (TSV) formatted file in the UTF-8
character set. The contents of each column is described in the first line in each file containing
headers. A ‘\N’ is used to denote that a particular field is missing or null for that title/name.<br>
The available datasets are as follows :<br>
* #### Title.akas.tsv.gz <br>
  * titleId (string) - a tconst, an alphanumeric unique identifier of the title
  * ordering (integer) – a number to uniquely identify rows for a given titleId
  * title (string) – the localized title
  * region (string) - the region for this version of the title
  * language (string) - the language of the title
  * types (array) - Enumerated set of attributes for this alternative title. One or more of the
  following: "alternative", "dvd", "festival", "tv", "video", "working", "original", "imdbDisplay".
  New values may be added in the future without warning
  * attributes (array) - Additional terms to describe this alternative title, not enumerated
  * isOriginalTitle (boolean) – 0: not original title; 1: original title
  Title.basics.tsv.gz
  * tconst (string) - alphanumeric unique identifier of the title
  * titleType (string) – the type/format of the title (e.g. movie, short, tvseries, tvepisode, video,
  etc)
  * primaryTitle (string) – the more popular title / the title used by the filmmakers on promotional
  materials at the point of release
  * originalTitle (string) - original title, in the original language
  * isAdult (boolean) - 0: non-adult title; 1: adult title
  * startYear (YYYY) – represents the release year of a title. In the case of TV Series, it is the
  series start year
  * endYear (YYYY) – TV Series end year. ‘\N’ for all other title types
  * runtimeMinutes – primary runtime of the title, in minutes
  * genres (string array) – includes up to three genres associated with the title
* #### Title.crew.tsv.gz
  * tconst (string) - alphanumeric unique identifier of the title
  * directors (array of nconsts) - director(s) of the given title
  * writers (array of nconsts) – writer(s) of the given title
* #### Title.episode.tsv.gz
  * tconst (string) - alphanumeric identifier of episode
  * parentTconst (string) - alphanumeric identifier of the parent TV Series
  * seasonNumber (integer) – season number the episode belongs to
  * episodeNumber (integer) – episode number of the tconst in the TV series
* #### Title.principals.tsv.gz
  * tconst (string) - alphanumeric unique identifier of the title
  * ordering (integer) – a number to uniquely identify rows for a given titleId
  * nconst (string) - alphanumeric unique identifier of the name/person
  * category (string) - the category of job that person was in
  * job (string) - the specific job title if applicable, else '\N'
  * characters (string) - the name of the character played if applicable, else '\N'
* #### Title.ratings.tsv.gz
  * tconst (string) - alphanumeric unique identifier of the title
  * averageRating – weighted average of all the individual user ratings
  * numVotes - number of votes the title has received
* #### Name.basics.tsv.gz
  * nconst (string) - alphanumeric unique identifier of the name/person
  * primaryName (string)– name by which the person is most often credited
  * birthYear – in YYYY format ● deathYear – in YYYY format if applicable, else '\N'
  * primaryProfession (array of strings)– the top-3 professions of the person
  * knownForTitles (array of tconsts) – titles the person is known for
  
### Use-Cases defined
* Relationship between the runtime and popularity of a TV Series.
* Popularity of a genre based on region.
* Analyze how the popularity of a TV series changed over time.
* Popularity of directors based on genre.
* Predict the movie's rating based on multiple factors such as genre, director.

### Integrity Constraints Identified
After all the cleaning and merging of the files is done, we went on to define rules to make sure whenever data operations such as updation, insertion are performed, data integrity isn’t overlooked. To achieve the same, we defined the following set of rules:
* title_id should be unique.
* startyear should not be zero 0
* runtimeMinutes should not be less than zero
* averageRating cannot be greater than 10 and smaller than or equal to zero.
