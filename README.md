java c
School   of Computing   and   Information   Systems 
COMP20005   Intro.   to   Numerical   Computation   in   C 
Semester   2,   2024 
Assignment   2 
Due: 4:00 pm Thursday 17th October 2024 
Version   1.0
1 Learning Outcomes 
In this   assignment, you will   demonstrate your   understanding   of arrays   and   structures,   and   use   them   together   with   functions.   You   will   further   practise   your   skills   in   program   design   and   debugging.
2 The Story... There   are   over   12   million   credit   cards   in   Australia,    and   the   number   is   over   7   billion   worldwide.    This   is   a goldmine   for   cybercriminals   who   make   unauthorised   payments   to   obtain   goods   or   services   (i.e.,    credit      card fraud).   In   the   2022-2023 financial   year, it   was   estimated   that   1.8   million   people   in   Australia   experienced   card fraud.       Banks   and   credit   card   companies   are   strongly   motivated   to   develop   anti-fraud   technologies.      They   prevented   two-thirds   of   the   attempted   card   fraud   in   the   UK   in   2018,    but   this   is   a   never-ending   war.There   are   various   anti-fraud   algorithms.   The   core   of   those   algorithms   are   rules   and   statistics   (now   advanced machine   learning   algorithms)   to   classify   whether   a   transaction   is   abnormal   and   likely   to   be   fraudulent.    For   example,    a   transaction   well   beyond   the   credit   limit   of   a   card   is   likely   to   be   fraudulent,    and    so   are   two   transactions   of the   same   card   issued   at   almost   the   same   time   but   from   two   different   cities.
3 Your Task 
In   this   assignment,   you   will   write   a   program   to   process   a   list   of   credit   card   and   transaction   records    (as   exemplified   below)   and   identify   fraudulent   transactions.      You   do   not   need   to    be    an    anti-fraud   expert.
fhlt2p      8000      500
hmqe2v      1000      800
q5g8d8    2000      1000
sqx7pb    20000      5000
swi6ea    250      100
@@@@@@@@@@
s34zzeup6b      q5g8d8    2024:09:01:04:52:46    548
lusmddyzp9      fhlt2p      2024:09:03:06:18:22      9198
vd00nc9qb8      fhlt2p      2024:09:07:08:42:03      72
0het8hcrda      sqx7pb      2024:09:10:12:10:53    610
toxesmipak      q5g8d8    2024:09:10:15:14:54      936
k3hn309eep      sqx7pb      2024:09:10:19:51:34    489
slvazil8t5      fhlt2p      2024:09:17:22:37:49      922
wkhispe89i      q5g8d8    2024:09:21:23:34:27    2809
yhnxcl0ked      hmqe2v    2024:09:26:23:12:08      433
adezmz9pqk      swi6ea      2024:09:26:23:17:09    200The   input   starts   with   a   list   of credit   card   records   sorted    by   card   ID.   There   are at least 1 and at most 50 cards.   Each   credit   card   occupies   one   line   with   three   fields   separated   by   a   single   whitespace:   unique   card   ID (6   alphanumeric   characters;   no   upper-case   letters),   daily   limit   (the total   amount that   can be   spent   in   a   day),   and   transaction   limit   (the   amount   that   can   be   spent   in   a   transaction).   Both   limits   are   positive   integers   that   can   be   represented   by   int   variables.   The   transaction   limit   does   not   exceed   the   daily   limit.
The   line    “@@@@@@@@@@”   indicates   the   end   of   credit   card   records   and   the   start   of transactions.The   transactions   are   sorted   by   date   and   time.   There   are at least 1 and at most 100 transactions.   Each transaction   occupies   one   line   with   four   fields   separated   by   a   single   whitespace:    unique   transaction   ID      (10   alphanumeric   characters;   no   upper-case   letters),   card   ID   (6   alphanumeric   characters;   no   upper-case   letters;   must have appeared in the card records), transaction   date   and time   (year:month:day:hour:minute:second,   four   digits   for   year   and   two   digits   for   each   of   the   other   components),   and   transaction   amount   (a   positive   integer,   for   simplicity).
You   may   assume   that   the   input   data   is    always   in   valid   format.    No    input   format    validity    checking   is    needed.
3.1          Stage 1 - Read the First Credit Card Record (6 Marks) 
Your   first   task   is   to   design   a   struct   to   represent   a   credit   card   record.    You   will   then   read   in   a   credit   card   record   from   the   input   data,   and   output   it   in   the   following   format   (where   “mac:”   is   the   command   prompt):
mac:      ./program      < test0 .txt
Stage      1
==========
Card      id:      fhlt2p
Daily      limit:      8000
Transaction      limit:      500
You   can   also   read   all   input   data   before   printing   out   for   Stage   1.   You   may   (and   should)   add   more   functions as   appropriate.
3.2          Stage 2 - Read the Rest of Credit Card Records (5 Marks) Next, continue to read all   credit   card   records.   You   need to   design   a   proper   data   structure   to   store   the   records   read.   An array will do the job nicely.   When this stage is   done,   your   program   should   output:   the   total   number   of   credit   card   records   read,   the   credit   card   with   the   largest   daily   limit    (if there   is   a   tie,   print   the   card   with   the   smallest   ID   among   the   tied   ones),   and   the   average   transaction   limit   per   card   (up   to   two   digits   after   the decimal   point,   by   using   “%.2f”   in printf()).   The   output   of this   stage   based   on the   sample   input   is:
Stage      2
==========
Number      of    credit    cards:      5
Card      with      the      largest      daily      limit:      sqx7pb
Average      transaction      limit:    1480   .00
3.3 Stage 3 - Read the Transactions (5 Marks) Your   third   task   is   to   design   a   struct   to   represent   a   transaction,   read   in 代 写COMP20005 Intro. to Numerical Computation in C Semester 2, 2024 Assignment 2R
代做程序编程语言  the   transactions,   store   them   in   another   array,   and   output   the   total   number   of   transactions   and   the   credit   card   with   the   largest   number   of   transactions   (if there   is   a   tie,   print   the   card   with   the   smallest   ID   among   the   tied   ones).    The   output   in   this   stage   for   the   sample   input   above   should   be:
Stage      3
==========
Number      of      transactions:    10
Card      with      the      largest      number      of      transactions:      fhlt2p
You   may   assume   that   all   credit   card   IDs   in   the   transactions   can   be   found   in   the   credit   card   records.
3.4 Stage 4 - Check for Fraudulent Transactions (4 Marks) The   next   stage   is   to   check   whether   a   transaction   maybe   fraudulent.   You   will   go   through   the   transactions.   For each   transaction,   you   need   to   check   if it   exceeds   the   transaction   limit   or   the   daily   limit   of the   corresponding   credit   card.
A   sample   output   given   the   input   example   above   is   (note   a   final   newline   character   ‘\n’   at   the   end):
Stage      4
==========
s34zzeup6b    WITHIN_BOTH_LIMITS
lusmddyzp9    EXCEED_BOTH_LIMITS    /*    9198    >      8000      and      9198      >      500      */
vd00nc9qb8    WITHIN_BOTH_LIMITS0het8hcrda    WITHIN_BOTH_LIMITStoxesmipak    WITHIN_BOTH_LIMITS  k3hn309eep    WITHIN_BOTH_LIMITS 
slvazil8t5    EXCEED_TRANS_LIMIT      /*    922    >    500    */
wkhispe89i    EXCEED_BOTH_LIMITS    /*    2809    >      2000      and      2809      >      1000      */
yhnxcl0ked    WITHIN_BOTH_LIMITS
adezmz9pqk    EXCEED_TRANS_LIMIT    /*    200      >      100      */For    a    challenge,    see    if   you    can      design      an      algorithm    that      only   needs      to   go      through      the      transactions      once    for   completing   Stage   4   .      Hint:       To    achieve    such    an    algorithm,    you    may    need    to    modify    the    credit    card    struct    to   store    additional   information.
4          Submission and Assessment 
This   assignment   is   worth   20%   of   the   final   mark.   A   detailed   marking   scheme   will   be   provided   on   LMS.Submitting your code. To   submit   your   code,   you   will   need   to:    (1)   Log   in   to   LMS   subject   site,    (2)   Nav-   igate   to “Assignment   2”   in   the “Assignments”   page,    (3)   Click   on “Load   Assignment   2   in   a   new   window”,   and   (4)   follow   the   instructions   on   the   Gradescope “Assignment   2”   page   and   click   on   the “Submit”   link   to make   a   submission.    You   can   submit    as   many   times   as   you   want   to.       Only    the    last    submission    made      before   the    deadline    will    be    marked.       Submissions   made   after   the   deadline   will   be   marked   with   late   penalties   as   de-   tailed   at   the   end   of this   section.   Do   not   submit   after   the   deadline   unless   a   late   submission   is   intended.   Two hidden   tests   will   be   run   for   marking   purposes.    Results   of   these   tests   will   be   released   after   the   marking   is   done.
You   can   (and   should)   submit   both early and often – to   check that your   program   compiles   correctly   on   our   test   system,   which   may   have   some   different   characteristics   to   your   own   machines.Testing on your own computer. You   will   be   given   a   sample   test   file   test0   .txt   and   the   sample   output   test0-output   .txt.   You   can test your   code   on your   own   machine with   the   following   command   and   compare   the output with   test0-output   .txt:
mac:    ./program    < test0.txt /* Here ‘<’ feeds the data from test0.txt into program */
Note   that   we   are   using   the   following   command   to   compile   your   code   on   the   submission   testing   system   (we name   the   source   code   file   program.c).
gcc      -Wall      -std=c17    -o      program      program   .c    -lmThe   flag   “-std=c17”   enables   the   compiler   to   use   a   modern   standard   of   the   C   language – C17.    To   ensure   that your   submission   works   properly   on   the   submission   system,   you   should   use   this   command   to   compile   your code   on   your   local   machine   as   well.
You   may   discuss   your   work   with   others,   but   what   gets   typed   into   your   program   must   be   individual   work, not from   anyone   else.
• Do not give   (hard   or   soft)   copies   of   your   work   to   anyone   else.
• Do not “lend” your   memory   stick   to   others.
• Do not leave   your   laptop   unlocked   in   the   lab   or   library.
• Do not upload   your   assignment   solutions   onto   Github   or   any   other   public   code   repositories.
•      Do not ask others to give   you   their   programs   “just   so   that   I   can   take   a   look   and   get   some   ideas,I   won’t   copy,   honest”   .The   best   way   to   help   your   friends   in   this   regard   is   to   say   a   very   firm    “no”   when   they   ask   for   a   copy   of,      or   to   see,   your   program,   pointing   out   that   your    “no”,    and   their    acceptance   of   that   decision,   is   the   only      thing   that   will   preserve   your   friendship.    A      sophisticated   program      that   undertakes      deep      structural      analysis      of C   code    identifying    regions    of   similarity    will    be    run    over    all    submissions    in       “compare    every    pair”    mode.       See https://academichonesty.unimelb.edu.au for   more information.Deadline:      Programs   not   submitted   by 4:00 pm Thursday 17th October 2024 will   lose   penalty   marks   at   the   rate   of   3   marks   per   day   or   part   day   late.    Late   submissions   after   4:00   pm   Sunday   20th   October   2024   will not be   accepted.



         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
