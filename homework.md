# SQL Homework

The local cinema are having a Marvel Movie Marathon! They have asked you to help maintain their database of movies with times and attendees.

## To access the database:

First, create a database called 'marvel'

```
# terminal
createdb marvel
```

Next, run the provided SQL script to populate your database:

```
# terminal
psql -d marvel -f marvel.sql
```

Use the supplied data as the source of data to answer the questions. Copy the SQL command you have used to get the answer, and paste it below the question, along with the result they gave.

## Questions

1.  Return ALL the data in the 'movies' table.
SELECT * FROM movies;

 id |                title                | year | show_time 
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 18:45
  2 | The Incredible Hulk                 | 2008 | 13:35
  3 | Iron Man 2                          | 2010 | 16:55
  4 | Thor                                | 2011 | 15:05
  5 | Captain America: The First Avenger  | 2011 | 20:05
  6 | Avengers Assemble                   | 2012 | 12:55
  7 | Iron Man 3                          | 2013 | 21:55
  8 | Thor: The Dark World                | 2013 | 12:45
  9 | Batman Begins                       | 2005 | 12:30
 10 | Captain America: The Winter Soldier | 2014 | 15:40
 11 | Guardians of the Galaxy             | 2014 | 22:20
 12 | Avengers: Age of Ultron             | 2015 | 21:55
 13 | Ant-Man                             | 2015 | 21:20
 14 | Captain America: Civil War          | 2016 | 16:15
 15 | Doctor Strange                      | 2016 | 23:50
 16 | Guardians of the Galaxy 2           | 2017 | 13:05
 17 | Spider-Man: Homecoming              | 2017 | 20:45
 18 | Thor: Ragnarok                      | 2017 | 15:20
 19 | Black Panther                       | 2018 | 12:45


2.  Return ONLY the name column from the 'people' table

SELECT name FROM people;

        name        
--------------------
 Stuart Black
 Euan Cunningham
 Mark Ditzel
 Tahnee Downie
 Molly Drumm
 Robbie Dumbrell
 Beata Ficek
 Joanna Gora
 Patrycja Graczyk
 Vicky Jackson-Five
 Marcin Jerwan
 Garry McCrum
 Gemma Percival
 Digory Philbrow
 Ricardo Ruiz
 Kirstin Ryan
 Mike Thorpe
 Raphael Ugha
 Emil Vaklinov
 Donald Trump


3.  Oops! Someone at CodeClan spelled Vicky's name wrong! Change it to reflect the proper spelling ('Vicky Jackson-Five' should be 'Vicky Jackson').

UPDATE people SET name = 'Vicky Jackson'
		WHERE name = 'Vicky Jackson-Five';
SELECT name FROM people;

UPDATE 1
       name       
------------------
 Stuart Black
 Euan Cunningham
 Mark Ditzel
 Tahnee Downie
 Molly Drumm
 Robbie Dumbrell
 Beata Ficek
 Joanna Gora
 Patrycja Graczyk
 Marcin Jerwan
 Garry McCrum
 Gemma Percival
 Digory Philbrow
 Ricardo Ruiz
 Kirstin Ryan
 Mike Thorpe
 Raphael Ugha
 Emil Vaklinov
 Donald Trump
 Vicky Jackson
(20 rows)


4.  Return ONLY your name from the 'people' table.

SELECT name FROM people
	WHERE name = 'Patrycja Graczyk';

name       
------------------
 Patrycja Graczyk
(1 row)	

5.  The cinema is showing 'Batman Begins', but Batman is DC, not Marvel! Delete the entry from the 'movies' table.

DELETE FROM movies
	WHERE title = 'Batman Begins';
SELECT * FROM movies;

DELETE 1
 id |                title                | year | show_time 
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 18:45
  2 | The Incredible Hulk                 | 2008 | 13:35
  3 | Iron Man 2                          | 2010 | 16:55
  4 | Thor                                | 2011 | 15:05
  5 | Captain America: The First Avenger  | 2011 | 20:05
  6 | Avengers Assemble                   | 2012 | 12:55
  7 | Iron Man 3                          | 2013 | 21:55
  8 | Thor: The Dark World                | 2013 | 12:45
 10 | Captain America: The Winter Soldier | 2014 | 15:40
 11 | Guardians of the Galaxy             | 2014 | 22:20
 12 | Avengers: Age of Ultron             | 2015 | 21:55
 13 | Ant-Man                             | 2015 | 21:20
 14 | Captain America: Civil War          | 2016 | 16:15
 15 | Doctor Strange                      | 2016 | 23:50
 16 | Guardians of the Galaxy 2           | 2017 | 13:05
 17 | Spider-Man: Homecoming              | 2017 | 20:45
 18 | Thor: Ragnarok                      | 2017 | 15:20
 19 | Black Panther                       | 2018 | 12:45
(18 rows)


6.  Create a new entry in the 'people' table with the name of one of the instructors.

INSERT INTO people (name) VALUES ('Alex B');
SELECT name FROM people;
INSERT 0 1
       name       
------------------
 Stuart Black
 Euan Cunningham
 Mark Ditzel
 Tahnee Downie
 Molly Drumm
 Robbie Dumbrell
 Beata Ficek
 Joanna Gora
 Patrycja Graczyk
 Marcin Jerwan
 Garry McCrum
 Gemma Percival
 Digory Philbrow
 Ricardo Ruiz
 Kirstin Ryan
 Mike Thorpe
 Raphael Ugha
 Emil Vaklinov
 Donald Trump
 Vicky Jackson
 Alex B
(21 rows)


7.  Donald Trump has decided to hijack our movie evening, Remove him from the table of people.

DELETE FROM people
	WHERE name = 'Donald Trump';
SELECT name FROM people;

DELETE 1
       name       
------------------
 Stuart Black
 Euan Cunningham
 Mark Ditzel
 Tahnee Downie
 Molly Drumm
 Robbie Dumbrell
 Beata Ficek
 Joanna Gora
 Patrycja Graczyk
 Marcin Jerwan
 Garry McCrum
 Gemma Percival
 Digory Philbrow
 Ricardo Ruiz
 Kirstin Ryan
 Mike Thorpe
 Raphael Ugha
 Emil Vaklinov
 Vicky Jackson
 Alex B
(20 rows)

8.  The cinema has just heard that they will be holding an exclusive midnight showing of 'Avengers: Infinity War'!! Create a new entry in the 'movies' table to reflect this.

INSERT INTO movies (title, year, show_time) VALUES ('Avengers: Infinity War', 2017, '00:00');
SELECT * FROM movies;

INSERT 0 1
 id |                title                | year | show_time 
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 18:45
  2 | The Incredible Hulk                 | 2008 | 13:35
  3 | Iron Man 2                          | 2010 | 16:55
  4 | Thor                                | 2011 | 15:05
  5 | Captain America: The First Avenger  | 2011 | 20:05
  6 | Avengers Assemble                   | 2012 | 12:55
  7 | Iron Man 3                          | 2013 | 21:55
  8 | Thor: The Dark World                | 2013 | 12:45
 10 | Captain America: The Winter Soldier | 2014 | 15:40
 11 | Guardians of the Galaxy             | 2014 | 22:20
 12 | Avengers: Age of Ultron             | 2015 | 21:55
 13 | Ant-Man                             | 2015 | 21:20
 14 | Captain America: Civil War          | 2016 | 16:15
 15 | Doctor Strange                      | 2016 | 23:50
 16 | Guardians of the Galaxy 2           | 2017 | 13:05
 17 | Spider-Man: Homecoming              | 2017 | 20:45
 18 | Thor: Ragnarok                      | 2017 | 15:20
 19 | Black Panther                       | 2018 | 12:45
 20 | Avengers: Infinity War              | 2017 | 00:00
(19 rows)


9.  The cinema would also like to make the Guardians movies a back to back feature. Find out the show time of "Guardians of the Galaxy" and set the show time of "Guardians of the Galaxy 2" to start two hours later.

SELECT show_time FROM movies
		WHERE title = 'Guardians of the Galaxy';
		
 show_time 
-----------
 22:20
(1 row)

UPDATE movies SET show_time = '24:20'
		WHERE title = 'Guardians of the Galaxy 2';
SELECT * FROM movies;


UPDATE 1
 id |                title                | year | show_time 
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 18:45
  2 | The Incredible Hulk                 | 2008 | 13:35
  3 | Iron Man 2                          | 2010 | 16:55
  4 | Thor                                | 2011 | 15:05
  5 | Captain America: The First Avenger  | 2011 | 20:05
  6 | Avengers Assemble                   | 2012 | 12:55
  7 | Iron Man 3                          | 2013 | 21:55
  8 | Thor: The Dark World                | 2013 | 12:45
 10 | Captain America: The Winter Soldier | 2014 | 15:40
 11 | Guardians of the Galaxy             | 2014 | 22:20
 12 | Avengers: Age of Ultron             | 2015 | 21:55
 13 | Ant-Man                             | 2015 | 21:20
 14 | Captain America: Civil War          | 2016 | 16:15
 15 | Doctor Strange                      | 2016 | 23:50
 17 | Spider-Man: Homecoming              | 2017 | 20:45
 18 | Thor: Ragnarok                      | 2017 | 15:20
 19 | Black Panther                       | 2018 | 12:45
 20 | Avengers: Infinity War              | 2017 | 00:00
 16 | Guardians of the Galaxy 2           | 2017 | 24:20
(19 rows)


## Extension

1.  Research how to delete multiple entries from your table in a single command.


DELETE FROM people WHERE name in ('Stuart Black','Joanna Gora');
SELECT * FROM people;

DELETE FROM movies WHERE id in (6, 8);
SELECT * FROM movies;

DELETE 2
 id |       name       
----+------------------
  2 | Euan Cunningham
  3 | Mark Ditzel
  4 | Tahnee Downie
  5 | Molly Drumm
  6 | Robbie Dumbrell
  7 | Beata Ficek
  9 | Patrycja Graczyk
 11 | Marcin Jerwan
 12 | Garry McCrum
 13 | Gemma Percival
 14 | Digory Philbrow
 15 | Ricardo Ruiz
 16 | Kirstin Ryan
 17 | Mike Thorpe
 18 | Raphael Ugha
 19 | Emil Vaklinov
 10 | Vicky Jackson
 21 | Alex B
(18 rows)

DELETE 2
 id |                title                | year | show_time 
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 18:45
  2 | The Incredible Hulk                 | 2008 | 13:35
  3 | Iron Man 2                          | 2010 | 16:55
  4 | Thor                                | 2011 | 15:05
  5 | Captain America: The First Avenger  | 2011 | 20:05
  7 | Iron Man 3                          | 2013 | 21:55
 10 | Captain America: The Winter Soldier | 2014 | 15:40
 11 | Guardians of the Galaxy             | 2014 | 22:20
 12 | Avengers: Age of Ultron             | 2015 | 21:55
 13 | Ant-Man                             | 2015 | 21:20
 14 | Captain America: Civil War          | 2016 | 16:15
 15 | Doctor Strange                      | 2016 | 23:50
 17 | Spider-Man: Homecoming              | 2017 | 20:45
 18 | Thor: Ragnarok                      | 2017 | 15:20
 19 | Black Panther                       | 2018 | 12:45
 20 | Avengers: Infinity War              | 2017 | 00:00
 16 | Guardians of the Galaxy 2           | 2017 | 24:20
(17 rows)

DELETE FROM movies WHERE year <> 2017;
SELECT * FROM movies;

DELETE 13
 id |           title           | year | show_time 
----+---------------------------+------+-----------
 17 | Spider-Man: Homecoming    | 2017 | 20:45
 18 | Thor: Ragnarok            | 2017 | 15:20
 20 | Avengers: Infinity War    | 2017 | 00:00
 16 | Guardians of the Galaxy 2 | 2017 | 24:20
(4 rows)




