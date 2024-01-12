# Assignment2

important modules required are
1. PLY package
2. requests

**Folder Structure**
- Assignment2
-   task1
-     -> taskA.py
-   task2
-     -> TaskB.py
-   task3
-     -> CountryRank.py
-     -> FlagBearer.py
-     -> CompareMedalTally.py

-   runner.py

Also each of the above folders contain their respective .html files

-   where to start?
**-   runner.py** is the main file which prompts the user to select one from given options
    1. Task A
    2. Task B
    3. Task C
    4. Exit
#....

  1. Task A does not take any input, it will output the list
            i)Host city
            ii)Motto
            iii)Nations
            iv)Athletes
            v)Events
            vi)Opening
            vii)Closing

     ###DEFINING TOKENS###
      tokens = ('BEGINTABLE',
      'OPENTABLE', 'CLOSETABLE', 'OPENROW', 'CLOSEROW',
      'OPENHEADER', 'CLOSEHEADER', 'OPENHREF', 'CLOSEHREF',
      'CONTENT', 'OPENDATA', 'CLOSEDATA' ,'OPENSPAN',
      'CLOSESPAN', 'OPENDIV', 'CLOSEDIV', 'OPENSTYLE', 'CLOSESTYLE','GARBAGE','data','OPENSUP','CLOSESUP')

     The above mentioned are the terminals for the grammar

     **start, skiptag, handleheader, dataCell, handlerow, table, empty, content, error** are the **Non- Terminals**

     def p_table(p):
      '''table : BEGINTABLE OPENTABLE OPENROW skiptag CLOSEROW handlerow '''
     this production skips first row and scrapes everything starting from second row

     you can see all other production rules in the respective files

2. Task B
     it takes one input
     After selecting **Task B**, runner.py calls **task2/taskB.py** and outputs the following data
                           i.For some five sports it will print:
                                                Venue
                                                Dates
                                                Competitors
                                                Number of events

                     tokens = ('BEGINTABLE','OPENHREF', 'CLOSEHREF',
          'CONTENT',  'OPEN_UL','CLOSE_UL','OPEN_OL','CLOSE_OL',
          'GARBAGE','dummy','data')
     The above are the terminals

           **skiptag, handleList, listitem, table, empty, content, error**
     The above are the set of Non-Terminals
4. Task C
     it will prompt user to select one from there options
     Choose option
                       1. Rank, Gold, Silver, Bronze
                       2. Flag Bearer
                       3. Medal Tally

       -> if you select option 1 i.e Rank, Gold, Silver, Bronze, it will output the details of top 10 countries and the no. of medals they own.
                               
                  ###DEFINING TOKENS###
                  tokens = ('BEGINTABLE','nbsp','OPENROW','CLOSEROW','OPENtableHEADER','CLOSEtableHEADER',
                  'OPENDATA','CLOSEDATA','OPENHEADER','CLOSEHEADER','CONTENT', 'OPENHREF','CLOSEHREF',
                  'GARBAGE','dummy','data')

             The above are the set of terminals

                     ###NON-TERMINALS
                   start, skiptag, hrefhandler, handleheader, dataCell, tableHEADERhandler, printnewline, handlerow, table, empty, content, error

             The above are the set of Non- Terminals
   
       -> for option 2.
               Asks the user to enter country code from a list of 10 countries
               select one number in the range[1-10]
               This will outputs the FlagBearer (opening) and FlagBearer (Closing) for that country.

                                               ###DEFINING TOKENS###
                              tokens = ('BEGINTABLE','nbsp',
                              'OPENDATA','CLOSEDATA','OPENHEADER','CLOSEHEADER','CONTENT', 
                              'GARBAGE','dummy','data')

               the above are the set of Terminals
                                ###NON-TERMINALS
                               start, skiptag, handleheader, dataCell, PRINTOPENING, PRINTCLOSING, table, nbsphandler, content, error

               The above are the set of non-terminals
   
             
   
       -> for option 3.
                Asks the user to enter any two country codes from a list of 10 countries
                select two numbers in the range[1-10]
                 **remember** input should be provided as a space separated values for example:  2 10

                This will provide the comparasion for those two countries. It will compare the type of medals they won and total medals
   
                               ###DEFINING TOKENS###
                                tokens = ('BEGINTABLE','nbsp','OPENROW','CLOSEROW','OPENtableHEADER','CLOSEtableHEADER',
                                'OPENDATA','CLOSEDATA','OPENHEADER','CLOSEHEADER','CONTENT', 'OPENHREF','CLOSEHREF',
                                'GARBAGE','dummy','data')
                the above are the set of Terminals
                                ###NON-TERMINALS
                               start, skiptag,hrefhandler, handleheader, dataCell, tableHEADERhandler, printnewline, handlerow, empty, content, error

               The above are the set of non-terminals
   



 
