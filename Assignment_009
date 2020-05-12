Q1 = " SELECT AVG(age) FROM Player;"

Q2 = "SELECT match_no,play_date FROM Match WHERE audience > 50000;"

Q3 = '''
        SELECT team_id,COUNT(win_lose) AS Won FROM MatchTeamDetails
        WHERE win_lose = 'W' GROUP BY team_id ORDER BY Won DESC,team_id ASC;
     '''        

Q4 = '''SELECT match_no,play_date FROM Match WHERE stop1_sec > (SELECT AVG(stop1_sec) FROM MATCH)
        ORDER BY match_no DESC;'''
        
Q5 = '''SELECT match_no, t.name, p.name FROM MatchCaptain AS mc
        INNER JOIN Team AS t ON  t.team_id = mc.team_id
        INNER JOIN Player AS p ON p.team_id = mc.team_id 
        WHERE (select p.player_id from player WHERE mc.captain = p.player_id)
        GROUP BY match_no,t.name
        ORDER BY match_no ASC, t.name ASC''';
        
Q6 = '''SELECT match_no, player.name, jersey_no FROM Match
        INNER JOIN Player ON player.player_id = match.player_of_match
        ORDER BY match_no ASC''';

Q7 = '''SELECT t.name,AVG(player.age) AS average_age from Player
        INNER JOIN Team  AS t ON t.team_id = player.team_id
        GROUP BY t.team_id HAVING AVG(player.age)>26 ORDER BY t.name ASC''';
        
Q8 = '''SELECT name, jersey_no, age, count(gd.goal_id) as goal_score from player as p
         INNER JOIN GoalDetails as gd on p.player_id = gd.player_id 
         GROUP BY p.player_id HAVING age<=27 ORDER BY goal_score DESC, name ASC'''; 
         
Q9 = '''SELECT team_id,(count(goal_id)*100.0)/(select count(goal_id) from goaldetails)
        from GoalDetails GROUP BY team_id''';

Q10 = '''SELECT AVG(s) from
      (select count(goal_id) as s from GoalDetails group by team_id)''';
      
Q11 = '''SELECT p.player_id, name, date_of_birth FROM Player as p
         where NOT EXISTS(select gd.player_id from goaldetails as gd where p.player_id = gd.player_id) order by p.player_id ASC''';

Q12 = '''SELECT name, m.match_no, audience, 
        audience - (select avg(audience) from Match join matchteamdetails as mt on mt.match_no = match.match_no where mt.team_id = t.team_id)
        from Match as m
        INNER JOIN MatchTeamDetails as mtd on mtd.match_no = m.match_no
        INNER JOIN Team as t ON t.team_id = mtd.team_id
        ORDER BY m.match_no ASC''';        
        
        
