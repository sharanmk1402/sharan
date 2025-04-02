1) UPDATE student SET TOTAL=MARKS1+MARKS2+MARKS3;
2) UPDATE student SET CGPA=(TOTAL/30);
3) SELECT * FROM student WHERE DOB LIKE '2003-__-__';
4) SELECT * FROM student WHERE BRANCH='MCA';
5) SELECT BRANCH,MAX(CGPA) FROM student GROUP BY BRANCH;
6) SELECT * FROM STUDENT WHERE NAME LIKE 'T%';
7) SELECT NAME FROM student WHERE NAME LIKE 'KR%';
8) DELETE FROM student WHERE USN='U01';
   
 2 22222222222222222222 --------------------------------------2
 
   1) SELECT * FROM students S, branch B WHERE S.BRANCH_ID=B.BRANCH_ID
AND S.SEM='2'AND B.BRANCH_NAME='MCA';
2) SELECT * FROM students WHERE USN NOT IN(SELECT USN FROM borrow);
3)  SELECT BW.USN, SEM, S.NAME, B.BRANCH_NAME, A.AUTHOR_NAME,
BW.BORROW_DATE FROM students S, branch B, book BK, author A, borrow BW
WHERE S.BRANCH_ID=B.BRANCH_ID AND S.SEM='2' AND
B.BRANCH_NAME='MCA' AND S.USN=BW.USN AND
BW.BOOK_ID=BK.BOOK_ID AND BK.BOOK_ID=BW.BOOK_ID AND
BK.AUTHOR_ID=A.AUTHOR_ID;
4) SELECT A.AUTHOR_NAME, COUNT(*) FROM author A
 JOIN book BK ON A.AUTHOR_ID = BK.AUTHOR_ID
 GROUP BY A.AUTHOR_ID, A.AUTHOR_NAME;
5) SELECT S.* FROM students S, borrow BW WHERE S.USN=BW.USN GROUP BY
BW.USN HAVING COUNT(BW.USN)>2;
6) SELECT * FROM students S WHERE EXISTS(SELECT BW.USN FROM
BORROW BW JOIN book BK ON BW.BOOK_ID=BK.BOOK_ID WHERE
BW.USN=S.USN GROUP BY USN HAVING COUNT(DISTINCT
AUTHOR_ID)>1);
7) SELECT BOOK_NAME FROM book ORDER BY BOOK_NAME DESC;
8)  SELECT * FROM students S, borrow BW, book B WHERE S.USN=BW.USN AND
BW.BOOK_ID=B.BOOK_ID GROUP BY PUBLISHER;

3333333-----------------------------------------------------------------------3

1) SELECT PL_NAME,TEAM_NAME,AGE FROM player P,TEAM T WHERE
P.TEAM_ID=T.TEAM_ID AND AGE=(SELECT MIN(AGE) FROM player);
2) SELECT * FROM stadium WHERE ST_ID IN(SELECT ST_ID FROM matchs
GROUP BY ST_ID HAVING COUNT(ST_ID)=(SELECT COUNT(ST_ID) FROM
matchs GROUP BY ST_ID ORDER BY ST_ID ASC LIMIT 1));
3) SELECT * FROM player WHERE PL_ID NOT IN( SELECT TEAM_CAPTAIN
FROM team) AND PL_ID IN(SELECT MAN_OF_MATCH FROM matchs GROUP
BY man_of_match HAVING COUNT(MAN_OF_MATCH)>=2);
4) SELECT * FROM team WHERE TEAM_ID IN (SELECT TEAM_WON FROM
matchs GROUP BY TEAM_WON HAVING COUNT(*) = (SELECT
MAX(win_count) FROM (SELECT TEAM_WON, COUNT(*) AS win_count
FROM matchs GROUP BY TEAM_WON) AS win_counts));
5) SELECT T.TEAM_ID, T.TEAM_NAME, COUNT(M.TEAM_WON) AS WINS
FROM TEAM T
JOIN matchs M ON T.TEAM_ID = M.TEAM_WON
GROUP BY T.TEAM_ID, T.TEAM_NAME
ORDER BY COUNT(M.TEAM_WON) DESC -- Repeat the COUNT() expression LIMIT 1;

444444-----------------------------------------------------44444

1) SELECT * FROM candidate WHERE CAN_ID IN(SELECT CAN_ID FROM contest CT,
constituency CS WHERE CT.CONST_ID=CS.CONST_ID GROUP BY CAN_ID HAVING
COUNT(DISTINCT(STATE))>1);
2) SELECT STATE FROM constituency GROUP BY STATE HAVING COUNT(*)=(SELECT
MAX(STATE_COUNT) FROM(SELECT COUNT(*) AS STATE_COUNT FROM
constituency GROUP BY STATE) AS X);
3) CREATE OR REPLACE PROCEDURE CHECKAGE(ID IN NUMBER,AGE IN
NUMBER) AS
BEGIN
IF AGE>=18 THEN
INSERT INTO VOTERS(VOTER_ID,AGE)VALUES(ID,AGE); ELSE
DBMS_OUTPUT.PUT_LINE('NOT AN ELIGIBLE VOTER'); END IF;
END;
4) DELIMITER $$
CREATE PROCEDURE GETNUMBEROFVOTERS(IN CONSTITUENCY_NAME
VARCHAR(255))
BEGIN
 DECLARE TOTAL_VOTERS INT;
 SELECT COUNT(*) INTO TOTAL_VOTERS
 FROM VOTER
 WHERE C_IDB IN (SELECT C_IDB FROM CONSTITUENCY WHERE C_NAME =
CONSTITUENCY_NAME);
 SELECT TOTAL_VOTERS AS NUMBER_OF_VOTERS;
END$$
DELIMITER ;
CALL GETNUMBEROFVOTERS(‘DHARWAD’);

5555555-----------------------------------------5555

1. SELECT STATE FROM places GROUP BY STATE HAVING COUNT(*) = ( SELECT
MAX(COUNTS) FROM
( SELECT COUNT(*) AS COUNTS FROM PLACES GROUP BY STATE ) AS
COUNTER );
2. SELECT * FROM places WHERE P_ID IN ( SELECT P_ID FROM GROUP BY
P_ID HAVING COUNT(*) = ( SELECT MAX(PLACE_COUNT) FROM ( SELECT
COUNT(*) AS PLACE_COUNT FROM GROUP BY P_ID ) AS SUBQUERY ) );
3. SELECTT.* FROM visits V, places P, tourist T WHERE V.P_ID = P.P_ID AND
V.T_ID = T.T_ID AND STATE = 'KARNATAKA' GROUP BY T.T_NAME, AGE,
COUNTRY HAVING COUNT(DISTINCT V.P_ID) = ( SELECT COUNT(*) FROM
places WHERE STATE = 'KARNATAKA');
4. SELECT T.NAME, AGE, COUNTRY FROM visits V, places P, tourist T WHERE
V.P_ID = P.P_ID AND V.T_ID = T.T_ID GROUP BY T.NAME, AGE, COUNTRY
HAVING COUNT(DISTINCT STATE) = (SELECT COUNT(DISTINCT STATE)
FROM places);
5. SELECT P.P_NAME, KM, HISTORY FROM V, places P, tourist T WHERE V.P_ID
= P.P_ID AND V.T_ID = T.T_ID GROUP BY P.P_NAME, KM, HISTORY HAVING
COUNT(DISTINCT COUNTRY) = (SELECT COUNT(DISTINCT COUNTRY)
FROM tourist);

xhtml----------------------------------------------------

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
    <title>JavaScript Problems</title>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <script type="text/javascript">
        // Function to display first n Fibonacci numbers
        function displayFibonacci() {
            let n = prompt("Enter a number to generate Fibonacci sequence:");
            n = parseInt(n);
            
            if (isNaN(n) || n <= 0) {
                alert("Please enter a positive integer.");
                return;
            }
            
            let fib = [0, 1];
            if (n === 1) {
                fib = [0];
            } else {
                for (let i = 2; i < n; i++) {
                    fib[i] = fib[i-1] + fib[i-2];
                }
            }
            
            alert("First " + n + " Fibonacci numbers:\n" + fib.join(", "));
        }
        
        // Function to display table of numbers and their squares
        function displaySquaresTable() {
            let n = prompt("Enter a number to generate squares table:");
            n = parseInt(n);
            
            if (isNaN(n) || n <= 0) {
                alert("Please enter a positive integer.");
                return;
            }
            
            let table = "Number\tSquare\n";
            table += "----------------\n";
            
            for (let i = 1; i <= n; i++) {
                table += i + "\t" + (i*i) + "\n";
            }
            
            alert("Table of numbers from 1 to " + n + " and their squares:\n\n" + table);
        }
    </script>
</head>
<body>
    <h1>JavaScript Problems</h1>
    
    <div>
        <h2>Problem A: Fibonacci Sequence</h2>
        <p>Click the button to display the first n Fibonacci numbers.</p>
        <button onclick="displayFibonacci()">Generate Fibonacci Numbers</button>
    </div>
    
    <div>
        <h2>Problem B: Squares Table</h2>
        <p>Click the button to display a table of numbers and their squares.</p>
        <button onclick="displaySquaresTable()">Generate Squares Table</button>
    </div>
</body>
</html>

----------------------------------------------------------------------------------

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
    <title>Stacked Paragraphs</title>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <style type="text/css">
        body {
            font-family: Arial, sans-serif;
            margin: 50px;
        }
        .paragraph-container {
            position: relative;
            width: 300px;
            height: 120px;
        }
        .stacked-paragraph {
            position: absolute;
            width: 280px;
            padding: 10px;
            background-color: #f0f0f0;
            border: 1px solid #ccc;
            border-radius: 5px;
            box-shadow: 2px 2px 5px rgba(0,0,0,0.2);
            transition: all 0.3s ease;
            overflow: hidden;
        }
        #para1 {
            z-index: 1;
            top: 0;
            height: 30px;
        }
        #para2 {
            z-index: 2;
            top: 20px;
            height: 30px;
        }
        #para3 {
            z-index: 3;
            top: 40px;
            height: 30px;
        }
        .stacked-paragraph:hover {
            height: auto;
            z-index: 10;
            background-color: #fff;
            box-shadow: 5px 5px 10px rgba(0,0,0,0.3);
        }
    </style>
    <script type="text/javascript">
        // Store original positions
        const originalPositions = {
            para1: { top: 0, zIndex: 1 },
            para2: { top: 20, zIndex: 2 },
            para3: { top: 40, zIndex: 3 }
        };

        function resetPositions(exceptId) {
            const paragraphs = ['para1', 'para2', 'para3'];
            paragraphs.forEach(id => {
                if (id !== exceptId) {
                    const para = document.getElementById(id);
                    para.style.top = originalPositions[id].top + 'px';
                    para.style.zIndex = originalPositions[id].zIndex;
                }
            });
        }

        function setupParagraphs() {
            const paragraphs = document.querySelectorAll('.stacked-paragraph');
            paragraphs.forEach(para => {
                para.addEventListener('mouseenter', function() {
                    this.style.top = '0';
                    this.style.zIndex = '10';
                    resetPositions(this.id);
                });
                para.addEventListener('mouseleave', function() {
                    // Return to original position
                    this.style.top = originalPositions[this.id].top + 'px';
                    this.style.zIndex = originalPositions[this.id].zIndex;
                });
            });
        }

        window.onload = setupParagraphs;
    </script>
</head>
<body>
    <h1>Stacked Paragraphs</h1>
    <div class="paragraph-container">
        <div id="para1" class="stacked-paragraph">
            <p>This is the first paragraph. It contains some sample text that will be partially hidden when stacked. When you hover over it, the full paragraph will be revealed.</p>
        </div>
        <div id="para2" class="stacked-paragraph">
            <p>This is the second paragraph. Notice how only a portion is visible when stacked. Hovering brings it to the top while maintaining the original stacking order when not hovered.</p>
        </div>
        <div id="para3" class="stacked-paragraph">
            <p>This is the third paragraph. The JavaScript ensures each paragraph returns to its original position rather than going to the bottom when you stop hovering over it.</p>
        </div>
    </div>
</body>
</html>

   
