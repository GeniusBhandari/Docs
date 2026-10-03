- TEST FOR SQL INJECTIONS :   use ' to check for any weaknesses
- XSS can be easily done by using <script></script> and others like on hover features in html or adding stuff in requests





Hacker 101 CTF 

MICRO CMS V2 ....(Im starting it from here because I figured it was somewhat easier before..) Oct 2
    -- On this Exercise I was quickly able to identify how the queries worked however I had some difficutly
    understanding how exactly exploit that.
    What I noticed was that when I executed ' the server will have some internal error aka its vunerable to SQL INJECTIONS
    how'll i break from it exactly??
    I have tried using stuff like name" OR 1=1 condition but it somehowis stringified ontheir end which I need to somehow bypass
    and make server return true on the assumed select line its using with SQL
    I have tried the usual ' method, which should have worked
    I have studied the owsap I think  yeah that sql injection introduction but thats not onside
    I found portswigger one after one and a half hours ffs and its very interesting 
    Can I possibly make it such that i'll get true access from just username I don't wanna bothering password
    I can use -- as comment in sqli but I need the first to be true somehow 
    I tried name' OR 'a'='a" -- didn't work an a couple of things too but eh eh eh
    Assuming query is like SELECT * WHERE admin = userinput AND password = userpasswordentered'
    can i tweak userinput aka name such that it'll ignore the later part of the line yes i can use -- but what about the admin itself
    or do i need some other way
    Ohh there is a section about subverting section log here turly nice nice
     I will try a basic again
     I tried the hints its 11 am rn been doing since nine for fks sake everything anyways second hint hints at union
     gtta see what that is from the academy thingy again
     Retrieving data has some of these ngl 
     I should be able to use ' UNION SELECT username, password FROM users-- lemme see assming its uername and pw for this nah internal server error
     why would i even retrieve data its not like im getting any data frm it i  js need the cookie im assuming that allows to get access to hidden page 
     I mean her hast o be a cookiechekc on their end

     So Its using union of some sorts how' di use union 
     UNION SELECT requires both tables to have exact number of columsand compatible data type 
     Im gnna see if i Can insert an account it in 
     Im assuimgn the response is like query is like
     Select * from username where username= 'entereinjectedname' AND password='enteredinjectedpassword';
     Now i know i can remove the later part using -- so I dont wanna touch the password part
     how'll i nject something to return true or may be inject a new user completely ??
     first we gtta add 
     ' to end the wuery so username = '' then what do we do ? 
     UNION to write another query? or can we js do '; SELECT 'test' AS PASSWORD;# or --??

     I am learning about union attacks 

     STep 1 figure out number of columns first using order by payload
     test' order by 1-- // no error 1 column exists
      if error occurts that mch colum doesn't exist
      to figured displayed columnss ... ' Union select 111,222,333,444,555 // (inputs depend on how many 
      columns were detected)---// WE figure which columns are displayed because only displayed ones can be seen on output
    To find all list of user name do 'UNION SELECT NULL,TABLE_NAME,NULL FRP ,INFORMATION_SCHEMA.TABLES--;

    I managed to get username to be correct using ' OR 1=1 ; injection it seems.... yaaay
    What I have figured at 6pm is that you see i need to merge the results i get with something a dumm y password to make servert think result has results since its only testing the result
    I am very sure I have to use UNION SELECT 'test';--
    I think app might me using number of rows returned
    i'l try
    js
    ' UNION select 'xyz';-- with xyz as password for payload
    Yaaay it worked I hav eno idea why though I even had to cheat to get the freaking code because heck m i supposed to find it 
    HAD TO SETUP WSL AND OTHER STUFF PLUS VM FOR BETTER WAY OF DOING THESE
    YESSIR ANYWAYS WE CONTINUE FROM OCTOBER FOUR