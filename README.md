1--------------------------------------------------------------------------------------------------

 UPDATE student SET TOTAL=MARKS1+MARKS2+MARKS3; 

UPDATE student SET CGPA=(TOTAL/30);
SELECT * FROM student WHERE DOB LIKE '2003-__-__';
 SELECT * FROM student WHERE BRANCH='MCA';
  SELECT BRANCH,MAX(CGPA) FROM student GROUP BY BRANCH;
  SELECT * FROM STUDENT WHERE NAME LIKE 'T%';
  SELECT NAME FROM student WHERE NAME LIKE 'KR%';
  DELETE FROM student WHERE USN='U01'; 


 2--------------------------------------------------------------------------------------

SELECT * FROM students S, branch B WHERE S.BRANCH_ID=B.BRANCH_ID AND 
S.SEM='2'AND B.BRANCH_NAME='MCA';
SELECT * FROM students WHERE USN NOT IN(SELECT USN FROM borrow);
SELECT BW.USN, SEM, S.NAME, B.BRANCH_NAME, A.AUTHOR_NAME, 
BW.BORROW_DATE FROM students S, branch B, book BK, author A, borrow BW 
WHERE S.BRANCH_ID=B.BRANCH_ID AND S.SEM='2' AND B.BRANCH_NAME='MCA' 
AND S.USN=BW.USN AND BW.BOOK_ID=BK.BOOK_ID AND 
BK.BOOK_ID=BW.BOOK_ID AND BK.AUTHOR_ID=A.AUTHOR_ID;  
SELECT A.AUTHOR_NAME, COUNT(*) FROM author A 
JOIN book BK ON A.AUTHOR_ID = BK.AUTHOR_ID 
GROUP BY A.AUTHOR_ID, A.AUTHOR_NAME;
 SELECT S.* FROM students S, borrow BW WHERE S.USN=BW.USN GROUP BY BW.USN 
HAVING COUNT(BW.USN)>2;
SELECT * FROM  students S WHERE EXISTS(SELECT BW.USN FROM BORROW BW JOIN 
book BK ON BW.BOOK_ID=BK.BOOK_ID WHERE BW.USN=S.USN GROUP BY USN 
HAVING COUNT(DISTINCT AUTHOR_ID)>1);
 SELECT BOOK_NAME FROM book ORDER BY BOOK_NAME DESC;
SELECT * FROM students S, borrow BW, book B WHERE S.USN=BW.USN AND 
BW.BOOK_ID=B.BOOK_ID GROUP BY PUBLISHER;


3  ---------------------------------------------------------------------

SELECT PL_NAME,TEAM_NAME,AGE FROM player P,TEAM T WHERE 
P.TEAM_ID=T.TEAM_ID AND AGE=(SELECT MIN(AGE) FROM player); 
 SELECT * FROM stadium WHERE ST_ID IN(SELECT ST_ID FROM matchs GROUP BY 
ST_ID HAVING COUNT(ST_ID)=(SELECT COUNT(ST_ID) FROM matchs GROUP BY ST_ID 
ORDER BY ST_ID ASC LIMIT 1)); 
SELECT * FROM player WHERE PL_ID NOT IN( SELECT TEAM_CAPTAIN FROM team) 
AND PL_ID IN(SELECT MAN_OF_MATCH FROM matchs GROUP BY man_of_match 
HAVING COUNT(MAN_OF_MATCH)>=2);
SELECT * FROM team WHERE TEAM_ID IN (SELECT TEAM_WON FROM matchs 
GROUP BY TEAM_WON HAVING COUNT(*) = (SELECT MAX(win_count) FROM 
(SELECT TEAM_WON, COUNT(*) AS win_count FROM matchs GROUP BY 
TEAM_WON) AS win_counts));
SELECT T.TEAM_ID, T.TEAM_NAME, COUNT(M.TEAM_WON) AS WINS FROM TEAM T 
JOIN matchs M ON T.TEAM_ID = M.TEAM_WON 
GROUP BY T.TEAM_ID, T.TEAM_NAME 
ORDER BY COUNT(M.TEAM_WON) DESC  -- Repeat the COUNT() expression LIMIT 1;


4-------------------------------------------------------------------------------

SELECT * FROM candidate WHERE CAN_ID IN(SELECT CAN_ID FROM contest CT, constituency 
CS WHERE CT.CONST_ID=CS.CONST_ID GROUP BY CAN_ID HAVING 
COUNT(DISTINCT(STATE))>1);
SELECT STATE FROM constituency GROUP BY STATE HAVING COUNT(*)=(SELECT 
MAX(STATE_COUNT) FROM(SELECT COUNT(*) AS STATE_COUNT FROM constituency GROUP 
BY STATE) AS X); 








 
