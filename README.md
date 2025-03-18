SELECT * FROM candidate WHERE CAN_ID IN(SELECT CAN_ID FROM contest CT, constituency CS WHERE CT.CONST_ID=CS.CONST_ID GROUP BY CAN_ID HAVING COUNT(DISTINCT(STATE))>1);
---------------------------------
SELECT STATE FROM constituency GROUP BY STATE HAVING COUNT(*)=(SELECT MAX(STATE_COUNT) FROM(SELECT COUNT(*) AS STATE_COUNT FROM constituency GROUP BY STATE) AS X);
-------------------------------
CREATE OR REPLACE PROCEDURE CHECKAGE(ID IN NUMBER,AGE IN NUMBER) AS
BEGIN
IF AGE>=18 THEN
INSERT INTO VOTERS(VOTER_ID,AGE)VALUES(ID,AGE); ELSE
DBMS_OUTPUT.PUT_LINE('NOT AN ELIGIBLE VOTER'); END IF;
END;
INSERT INTO VOTERS VALUES(10,’RAZAK’,12,’DHARWAD’,1);
INSERT INTO VOTERS VALUES(60,’RAZAK’,21,’DHARWAD’,1);
----------------------------
DELIMITER $$

CREATE PROCEDURE GETNUMBEROFVOTERS(IN CONSTITUENCY_NAME VARCHAR(255))
BEGIN
    DECLARE TOTAL_VOTERS INT;
    SELECT COUNT(*) INTO TOTAL_VOTERS
    FROM VOTER
    WHERE C_IDB IN (SELECT C_IDB FROM CONSTITUENCY WHERE C_NAME = CONSTITUENCY_NAME);      
    SELECT TOTAL_VOTERS AS NUMBER_OF_VOTERS;
END$$

DELIMITER ;

CALL GETNUMBEROFVOTERS(‘DHARWAD’);
----------------------------------
DELIMITER $$

CREATE TRIGGER UPDATE_VOTER_COUNT_AFTER_INSERT
AFTER INSERT ON VOTER
FOR EACH ROW
BEGIN
    -- UPDATE THE "NUM_VOTERS" FIELD IN THE "CONSTITUENCY" TABLE
    UPDATE CONSTITUENCY
    SET NO_OF_VOTERS = NO_OF_VOTERS + 1
    WHERE C_ID = NEW.C_ID;
END$$

DELIMITER ;
INSERT INTO VOTER VALUES(80,’NITIN’,23,’MALGI’,1);
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

<!DOCTYPE html>
<head>
    <meta charset="UTF-8">
    <title>Fibonacci and Square Table</title>
    <script type="text/javascript">
        function fibonacci() {
            var n = prompt("Enter a number to display the first n Fibonacci numbers:");
            n = parseInt(n);
            var fib = [0, 1];
            for (var i = 2; i < n; i++) {
                fib[i] = fib[i - 1] + fib[i - 2];
            }
            var fibNumbers = "The first " + n + " Fibonacci numbers are:\n";
            for (var i = 0; i < n; i++) {
                fibNumbers += fib[i] + "\n";
            }
            alert(fibNumbers);
        }

        function squaresTable() {
            var n = prompt("Enter a number to display a table of numbers and their squares:");
            n = parseInt(n);
            var table = "Number | Square\n";
            table += "-----------------\n";
            for (var i = 1; i <= n; i++) {
                table += i + "     | " + (i * i) + "\n";
            }
            alert(table);
        }
    </script>
</head>
<body>
    <h1>Fibonacci and Squares Table</h1>
    <button onclick="fibonacci()">Show Fibonacci Numbers</button><br><br>
    <button onclick="squaresTable()">Show Squares Table</button>
</body>
</html>


xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

1	SELECT STATE FROM places GROUP BY STATE HAVING COUNT(*) = ( SELECT MAX(COUNTS) FROM 
( SELECT COUNT(*) AS COUNTS FROM PLACES GROUP BY STATE ) AS COUNTER ); 
--------------------------------
2	SELECT * FROM places  WHERE P_ID IN ( SELECT P_ID FROM  GROUP BY P_ID HAVING COUNT(*) = ( SELECT MAX(PLACE_COUNT) FROM ( SELECT COUNT(*) AS PLACE_COUNT FROM  GROUP BY P_ID ) AS SUBQUERY ) );
	------------------------------
	3 3.	SELECTT.* FROM  visits V, places  P, tourist T WHERE V.P_ID = P.P_ID AND V.T_ID = T.T_ID AND STATE = 'KARNATAKA' GROUP BY T.T_NAME, AGE, COUNTRY HAVING COUNT(DISTINCT V.P_ID) = ( SELECT COUNT(*) FROM places WHERE STATE = 'KARNATAKA');
-------------------------------
4.	SELECT T.NAME, AGE, COUNTRY FROM  visits V, places  P, tourist  T WHERE V.P_ID = P.P_ID AND V.T_ID = T.T_ID GROUP BY T.NAME, AGE, COUNTRY HAVING COUNT(DISTINCT STATE) = (SELECT COUNT(DISTINCT STATE) FROM places);
-------------------------------
5.	SELECT P.P_NAME, KM, HISTORY FROM  V, places  P, tourist  T WHERE V.P_ID = P.P_ID AND V.T_ID = T.T_ID GROUP BY P.P_NAME, KM, HISTORY HAVING COUNT(DISTINCT COUNTRY) = (SELECT COUNT(DISTINCT COUNTRY) FROM tourist);


xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx


<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
    <title>Stack Ordering</title>
    <!-- Reduced CSS -->
    <style type="text/css">
        .layer {
            border: solid thick black;
            padding: 10px;
            width: 300px;
            height: 200px;
            position: absolute;
            z-index: 0;
        }
        #layer1 { background-color: brown; top: 100px; left: 200px; }
        #layer2 { background-color: gray; top: 120px; left: 220px; }
        #layer3 { background-color: white; top: 140px; left: 240px; }
    </style>
</head>
<body>
    <script type="text/javascript">
        var topLayer = "layer3";
        // Function to bring the chosen layer to the top
        function mover(toTop) {
            document.getElementById(topLayer).style.zIndex = "0";
            document.getElementById(toTop).style.zIndex = "1";
            topLayer = toTop;
        }
    </script>
    <p id="layer1" class="layer" onmouseover="mover('layer1');">This is the last layer</p>
    <p id="layer2" class="layer" onmouseover="mover('layer2');">This is the middle layer</p>
    <p id="layer3" class="layer" onmouseover="mover('layer3');">This is the first layer</p>
</body>
</html>







