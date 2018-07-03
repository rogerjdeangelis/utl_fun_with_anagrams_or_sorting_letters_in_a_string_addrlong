# utl_fun_with_anagrams_or_sorting_letters_in_a_string_addrlong
Fun with anagrams or sorting letters in a string addrlong  Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverflow SAS community.


    Fun with anagrams or sorting letters in a string addrlong;

    Lets see what anagrams we can find for the word SLATE

     Same result in WPS and SAS


    INPUT
    =====

      %let word=AELST;  * slate in alphabetical order


      WORD dictionary

      LUP.WRD total obs=427,082

              WRD

        13    AARDVARK
        14    AARDVARKS
        15    AARDWOLF
        16    AARDWOLVES
        17    AARGH
        18    AARON


      List of words in expanded English Dictionary

        Download from or use the many open source dictionaries on the web

         This is a very greedy dictionary
         https://www.dropbox.com/s/vow5x2ubxuzcai7/wrd.zip?dl=0
         or
         https://tinyurl.com/y7636pt7
         https://github.com/rogerjdeangelis/utl_fun_with_anagrams_or_sorting_letters_in_a_string_addrlong/blob/master/wrd.zip

         github
         https://tinyurl.com/yclm62lv
         https://github.com/rogerjdeangelis/utl_fun_with_anagrams_or_sorting_letters_in_a_string_addrlong


    PROCESS
    =======

    libname lup "d:/lup"; * lookup dictionaries;

    data want;

      retain src "AELST" org "SLATE";

      array bytes[5] $1 byte1-byte5;

      set lup.wrd(where=(length(wrd)=5));

      call pokelong (wrd, addrlong (byte1)) ;
      call sortc(of byte1-byte5);
      wrdOrd=peekclong (addrlong (byte1) , 5);

      if wrdOrd=src;

      keep org wrd;

    run;quit;


    OUTPUT
    ======

     WORK.WANT total obs=13

        ORG      WRD

       SLATE    ASTEL   Alfred the mentioned a tear shaped rock as an astel
       SLATE    LEAST
       SLATE    LEATS   Brit a trench or ditch that conveys water to a mill wheel
       SLATE    SALET   A helmet, also sometimes called a salade or celate.
       SLATE    SETAL   A stiff hair, bristle, or bristlelike process or part on an organism

       SLATE    SLATE

       SLATE    STALE
       SLATE    STEAL
       SLATE    STELA
       SLATE    TAELS   The TEALS program was started in 2009 by a Microsoft engineer
       SLATE    TALES
       SLATE    TEALS   A weight used in China and East Asia
       SLATE    TESLA

    *                _               _       _
     _ __ ___   __ _| | _____     __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \   / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/  | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|   \__,_|\__,_|\__\__,_|

    ;

     %let word=AELST;  * slate in alphabetical order

     download word dictionary
     https://www.dropbox.com/s/vow5x2ubxuzcai7/wrd.zip?dl=0

    *          _       _   _
     ___  ___ | |_   _| |_(_) ___  _ __
    / __|/ _ \| | | | | __| |/ _ \| '_ \
    \__ \ (_) | | |_| | |_| | (_) | | | |
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|

    ;

    SAS see process;

    * wps;
    %utl_submit_wps64('
    libname wrk sas7bdat "%sysfunc(pathname(work))";
    libname lup "d:/lup";

    data want;

      retain src "AELST" org "SLATE";

      array bytes[5] $1 byte1-byte5;

      set lup.wrd(where=(length(wrd)=5));

      call pokelong (wrd, addrlong (byte1)) ;
      call sortc(of byte1-byte5);
      wrdOrd=peekclong (addrlong (byte1) , 5);

      if wrdOrd=src;

      keep org wrd;

    run;quit;
    proc print;
    run;quit;
    ');

