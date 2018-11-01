# utl-normalize-a-wide-table-into-a-variable-x-value-table
Normalize a wide table into a variable x value table.

    Normalize a wide table into a variable x value table                                                          
                                                                                                                  
    github                                                                                                        
    https://tinyurl.com/yddywfxh                                                                                  
    https://github.com/rogerjdeangelis/utl-normalize-a-wide-table-into-a-variable-x-value-table                   
                                                                                                                  
    https://tinyurl.com/yacu8ucl                                                                                  
    https://communities.sas.com/t5/SAS-Programming/Put-all-the-rows-in-a-table-in-a-single-column/m-p/509708      
                                                                                                                  
    utl_gather (this is a useful macro)                                                                           
    Alea Iacta                                                                                                    
    https://github.com/clindocu                                                                                   
                                                                                                                  
    my macros                                                                                                     
    https://tinyurl.com/y9nfugth                                                                                  
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories                    
                                                                                                                  
                                                                                                                  
    INPUT                                                                                                         
    =====                                                                                                         
                                                                                                                  
     SASHELP.CLASS total obs=19                                                                                   
                                                                                                                  
      NAME       SEX    AGE    HEIGHT    WEIGHT                                                                   
                                                                                                                  
      Alfred      M      14     69.0      112.5                                                                   
      Alice       F      13     56.5       84.0                                                                   
      Barbara     F      13     65.3       98.0                                                                   
      .....                                                                                                       
      Ronald      M      15     67.0      133.0                                                                   
      Thomas      M      11     57.5       85.0                                                                   
      William     M      15     66.5      112.0                                                                   
                                                                                                                  
                                                                                                                  
    EXAMPLE OUTPUT                                                                                                
    ==============                                                                                                
                                                                                                                  
     WORK.WANT total obs=76                                                                                       
                                                                                                                  
      NAME       VARIABLE    VALUE    _COLFORMAT    _COLTYP                                                       
                                                                                                                  
      Alfred      SEX        M         $1.             C                                                          
      Alfred      AGE        14        BEST12.         N                                                          
      Alfred      HEIGHT     69        BEST12.         N                                                          
      Alfred      WEIGHT     112.5     BEST12.         N                                                          
                                                                                                                  
      Alice       SEX        F         $1.             C                                                          
      Alice       AGE        13        BEST12.         N                                                          
      Alice       HEIGHT     56.5      BEST12.         N                                                          
      Alice       WEIGHT     84        BEST12.         N                                                          
      ....                                                                                                        
      William     SEX        M         $1.             C                                                          
      William     AGE        15        BEST12.         N                                                          
      William     HEIGHT     66.5      BEST12.         N                                                          
      William     WEIGHT     112       BEST12.         N                                                          
                                                                                                                  
                                                                                                                  
    PROCESS                                                                                                       
    =======                                                                                                       
                                                                                                                  
     %utl_gather(sashelp.class,variable,value,name,want,valformat=$10.,withformats=Y);                            
                                                                                                                  
     Note is is the first step in a normalized scheme. _colformat, variable and _coltyp should be                 
     moved to another table and a foreign key maybe (1,2,3,4,5) for each name.                                    
                                                                                                                  
     1=> links to  SEX          $1.   C                                                                           
     2=> links to  HEIGHT   BEST12.   N                                                                           
                                                                                                                  
                                                                                                                  
