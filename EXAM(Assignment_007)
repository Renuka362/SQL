Q1 = "SELECT COUNT(id) FROM Movie WHERE year < 2000;"

Q2 = "SELECT AVG(rank) FROM Movie WHERE year = 1991;"

Q3 = "SELECT MIN(rank) FROM Movie WHERE year = 1991;"

Q4 = "SELECT fname,lname FROM Actor INNER JOIN Cast ON id = pid WHERE mid = 27;"

Q5 = "SELECT COUNT(mid) FROM Actor INNER JOIN Cast ON id = pid WHERE fname='Jon' AND lname='Dough';"

Q6 = "SELECT name FROM Movie WHERE (name LIKE 'Young Latin Girls %') AND (year BETWEEN 2003 AND 2006);"

Q7 = '''SELECT fname,lname 
        FROM Director INNER JOIN MovieDirector ON Director.id = MovieDirector.did 
        INNER JOIN Movie ON Movie.id = MovieDirector.mid 
        WHERE Movie.name LIKE 'Star Trek%';'''

Q8 = '''SELECT name FROM Movie INNER JOIN Cast ON `Movie`.id = `Cast`.mid
        INNER JOIN Actor ON `Actor`.id = `Cast`.pid
        INNER JOIN MovieDirector ON `MovieDirector`.mid = `Movie`.id
        INNER JOIN Director ON `MovieDirector`.did = `Director`.id
        WHERE (Actor.fname = 'Jackie (I)' AND Actor.lname= 'Chan') AND (Director.fname = 'Jackie (I)' AND Director.lname = 'Chan')
        ;'''
        
Q9 = '''SELECT fname,lname FROM Director INNER JOIN MovieDirector ON Director.id=MovieDirector.did
        INNER JOIN Movie ON Movie.id=MovieDirector.mid
        WHERE year = 2001 GROUP BY did HAVING COUNT(mid) >= 4 ORDER BY fname ASC,lname DESC;'''
        
Q10 = "SELECT gender,COUNT(gender) FROM Actor GROUP BY(gender) ORDER BY gender ASC;"

Q11 = '''SELECT DISTINCT m1.name,m2.name,m1.rank,m1.year FROM Movie m1,Movie m2 
         WHERE (m1.year = m2.year AND m1.rank = m2.rank) AND (m1.name != m2.name) 
         ORDER BY m1.name ASC LIMIT 100;'''

Q12 = '''SELECT  fname,year,AVG(rank) FROM Actor INNER JOIN Cast ON `Actor`.id = `Cast`.pid 
         INNER JOIN Movie ON  `Movie`.id = `Cast`.mid GROUP BY year,`Actor`.id ORDER BY fname ASC,year DESC LIMIT 100;'''
         
Q13 = '''SELECT Actor.fname,Director.fname,AVG(rank) AS score FROM Actor INNER JOIN Cast 
         ON `Actor`.id = `cast`.pid INNER JOIN Movie ON `Movie`.id = `Cast`.mid
         INNER JOIN MovieDirector ON `MovieDirector`.mid = `Movie`.id 
         INNER JOIN Director ON `Director`.id = `MovieDirector`.did 
         GROUP BY Actor.id,Director.id HAVING COUNT(Movie.id) >= 5
         ORDER BY score DESC,Director.fname ASC,Actor.fname DESC LIMIT 100;'''
            






