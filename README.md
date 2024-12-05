# soundtrack_case

Data Engineering Case
---------------------

Soundtrack Your Brand needs to pay the music rightholders, artists and songwriters, royalties for
the use of their music. This is done through the licensors that represent them; record labels,
publishers and collecting societies.

One important part of the royalty calculation is to determine the market share of the different
licensors in different markets/countries. This case is a simplified version of that calculation.
The market share of a specific licensor is calculated as the number of plays/streams in the country
of the music represented by the licensor divided by the total of all plays in the country. To not
have the market share affected by short plays, like someone skipping around between tracks, only
plays that lasted for at least 60 seconds are included in the calculation.


## Example

Track A1 is represented by Licensor A and is played 1 time in Sweden, Track A2 is also represented
by Licensor A and is played 2 times in Sweden. Track B1 is represented by Licensor B and is played
2 times in Sweden, but only 1 of the plays is longer than 60 seconds. Then the market share of
Licensor A in Sweden is 75% while the market share of Licensor B is 25%.


## Assignment

The assignment is to calculate the market share in the United States, Sweden, Germany and the United
Kingdom given data provided in CSV files. The presentation of the results is not important as long
as it is readable; text or CSV file or terminal output is all fine.

We would like you to complete this task before we meet; use whatever language and tools you are
comfortable with as long as you can share it with us, show and explain what it does. When we meet
we will spend some time discussing your solution. However we would like to focus on talking about
how you would implement a solution to the problem that would scale to handle billions of plays, up
to 100 million tracks, 100.000's of locations, 100's of licensors and countries. What we might like
to discuss, depending on your profile, is your approach to things like:

* What tools and methodologies to use to make writing data processing systems on that scale manageable

- Different tools means different purposes -

- Spark - solid foundations for large scale data processing
    High complexity and learning curve, 



    - Motherduck - Duckdb



* How to optimize execution time and/or resource usage of distributed data processing



* How to test large scale data processing systems


* How to manage orchestration and scheduling of many data processing jobs
    
    Airflow + Spark

    Prefect




* How to monitor data processing jobs for failures and data quality

    Different levels of monitoring -

    dbt and custom data tests according to table behaviour

    dbt packages - 
        elementary 
        great expectations

    For logs
    prometheus
    grafana
    ELK stack
    kibana

    Logs, metrics, alerts, dashboards, etc.


* How to manage varying quality of data, e.g. missing, late or incorrect; how to avoid it, design for it,
  monitor it and/or fix it, technically and/or process-wise


* How to serve results of data processing jobs to a web or mobile app through an API in an efficient way


* How to work with stakeholders in assessing needs and requirements for implementing new datasets and/or metrics

The data needed for the assignment is divided into three files:

### plays.csv

This file contains stream/play events, it references the location that was playing as well as the
track that was played by id. It also includes the number of milliseconds that the track was played.

```csv
location_id,track_id,played_ms
7edf93bd-3e...,83fdfe8c-d3...,103557
115b6d35-0f...,edf08cbc-b9...,48775
```

### location.csv

This file contains information about the locations playing music, in particular the two letter
country-code where it is located. It is keyed by the id referenced in plays.csv.

```csv
id,country
e1365905-a2...,SE
7edf93bd-3e...,GB
```

### tracks.csv

This file contains metadata about the available music tracks, in particular which licensor that
owns/represents the rights of the tracks. It is keyed by the id referenced in plays.csv. Note that
some ids referenced in plays.csv might be missing, this is intentional; the data isn't always
perfect. Remember that all plays (over 60 seconds) should be included in the market share
calculation denominator, regardless of whether we know which licensor who owns it.

```csv
id,licensor
65fc9e2b-15...,Universe Muzak Corp.
1b377c09-ef...,Werner Licensing
```
readme.md
Displaying readme.md.