Which HTML tag is used to define a table?
<table>

Which of the following is correct for creating an anchor link to a HTML element with the id attribute, id=section1 within the same page?
<a href=#section1>Go to Section 1</a>

Which is the correct syntax for a paragraph in HTML?
<p>Text</p>

Using proper HTML syntax, can the <p> tag be used without a closing tag?
No, it must always have a closing tag.

What does the <div> tag represent in HTML?
A container for grouping and styling content

How many levels of headings does HTML support?
6

Which HTML tag is used to create an ordered list?
<ol>

How is a semi-transparent black with 50% opacity written in RGBA?
rgba(0, 0, 0, 0.5)

Which tag is used to embed an image in an HTML document?
<img>

Which tag is used to make text bold in HTML?
<b>

How can you make a link not clickable?
Remove the href attribute.

Q11:
1. Style the villian class:

Add a a 1px solid brown border.
Set the background color to black.
Align the text to the center.
2. Style the minion id:

Make the text bold. 
Make the text size to 16px. 
Make the text color #FFF. 

EXTERNAL CSS:
/* 1. Style the villian class */
.villian {
    border: 1px solid brown;
    background-color: black;
    text-align: center;
}

/* 2. Style the minion id */
#minion {
    font-weight: bold;
    font-size: 16px;
    color: #FFF;
}

Q12:
1. Style the header:

Set the background color to green.
Make the text color rgb(255,255,255).
Align the text to the left.
Make the text bold
Make the text uppercase.
Set the padding to 10px
2. Style the footer:

Set the background color to hotpink.
Make the text color #0000FF 
Align the text to the center.
Set the padding to 20px

EXTERNAL CSS:
/* 1. Style the header */
header {
    background-color: green;
    color: rgb(255, 255, 255);
    text-align: left;
    font-weight: bold;
    text-transform: uppercase;
    padding: 10px;
}

/* 2. Style the footer */
footer {
    background-color: hotpink;
    color: #0000FF;
    text-align: center;
    padding: 20px;
}

Q13:
CREATE TABLE SCHOOL(
SCH_ID int,
SCH_NAME nchar(30),
SCH_PHONE nchar(8),
DIRECTOR int,
CONSTRAINT SCH_PK PRIMARY KEY (SCH_ID)
)

Q14:
CREATE TABLE STAFF(
STAFF_ID int,
NAME nchar(30),
IC_NO nchar(10),
ADDRESS nchar(70),
PHONE nchar(8),
POSITION nchar(30),
HIRE_DATE datetime2,
SALARY decimal(7,2),
SCH_ID int,
CONSTRAINT STAFF_PK PRIMARY KEY (STAFF_ID)
)

Q15:
ALTER TABLE SCHOOL
ADD CONSTRAINT SCH_STAFF_FK FOREIGN KEY (DIRECTOR)
REFERENCES STAFF(STAFF_ID)

Q16:
CREATE TABLE ROOM(
ROOM_NO nchar(5),
BLK_NO nchar(20),
ADDRESS nchar(70),
CONSTRAINT ROOM_PK PRIMARY KEY(ROOM_NO)
)

Q17:
CREATE TABLE RENT_DETAIL(
RD_ID int,
RSTART_DATE datetime2,
REND_DATE datetime2,
RFEES decimal(7,2),
ROOM_NO nchar(5),
STAFF_ID int,
CONSTRAINT RD_PK PRIMARY KEY (RD_ID),
CONSTRAINT RD_ROOM_FK FOREIGN KEY (ROOM_NO) REFERENCES ROOM(ROOM_NO),
CONSTRAINT RD_STAFF_FK FOREIGN KEY (STAFF_ID) REFERENCES STAFF(STAFF_ID)
);

Q18:
CREATE TABLE PAYMENT(
P_ID int,
P_TYPE nchar(10),
P_DATE datetime2,
P_AMOUNT decimal(7,2),
DESCRIPTION nchar(50),
RD_ID int,
FINANCE_STAFF int,
CONSTRAINT PAYMENT_PK PRIMARY KEY(P_ID),
CONSTRAINT PAYMENT_RD_FK FOREIGN KEY(RD_ID) REFERENCES RENT_DETAIL(RD_ID),
CONSTRAINT PAYMENT_STAFF_FK FOREIGN KEY(FINANCE_STAFF) REFERENCES STAFF(STAFF_ID)
);

Q19:
INSERT INTO SCHOOL (SCH_ID,SCH_NAME,SCH_PHONE)
VALUES 
(1,'ENG',61234567), 
(2,'BUS',61234568);

Q20:
INSERT INTO STAFF (STAFF_ID,NAME,POSITION,SCH_ID) 
VALUES
(1,'SAM CHIN','DIRECTOR',1),
(2,'LILY WHITE','DIRECTOR',2),
(3,'JOHN TAN','FINANCE STAFF',1),
(4,'HENRY POH','LECTURER',1),
(5,'LIU SHU QI','LECTURER',2);

Q21:
UPDATE SCHOOL
SET DIRECTOR = 1
WHERE SCH_ID = 1;

UPDATE SCHOOL
SET DIRECTOR = 2
WHERE SCH_ID = 2;

Q22:
INSERT INTO ROOM (ROOM_NO,BLK_NO,ADDRESS)
VALUES
('SA501',43,'43 TAMPINES AVE 1'),
('SA607',45,'45 TAMPINES AVE 1');

Q23:
INSERT INTO RENT_DETAIL(RD_ID,RSTART_DATE,REND_DATE,ROOM_NO,STAFF_ID)
VALUES
(1, GETDATE(), DATEADD(YEAR, 1, GETDATE()), 'SA501', 4),
(2, GETDATE(), DATEADD(YEAR, 2, GETDATE()), 'SA607', 5);

Q24:
INSERT INTO PAYMENT (P_ID,P_TYPE,P_DATE,RD_ID,FINANCE_STAFF)
VALUES
(1,'GIRO',GETDATE(),1,3),
(2,'SALARY',GETDATE(),2,3);

Q25:
SELECT SCHOOL.SCH_NAME, STAFF.NAME, RENT_DETAIL.REND_DATE, ROOM.BLK_NO, PAYMENT.P_TYPE
FROM SCHOOL, STAFF, RENT_DETAIL, ROOM, PAYMENT
WHERE SCHOOL.SCH_ID = STAFF.SCH_ID
AND STAFF.STAFF_ID = RENT_DETAIL.STAFF_ID
AND RENT_DETAIL.ROOM_NO = ROOM.ROOM_NO
AND RENT_DETAIL.RD_ID = PAYMENT.RD_ID;









