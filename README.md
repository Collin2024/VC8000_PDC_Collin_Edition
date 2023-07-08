# The-VC-8000-PDC-Collin-Edition
The VC 8000 PDC Collin Edition

PDC means Personal Decimal Computer

A message from the author of this project

To whom it may concern
This is a term project that I did while I was a student (sophmore) at Ramapo College in the CMPS 361 SOFTWARE_DESIGN course
I will leave the notes on the implementation for reference for anyone looking at how it works. Not only is this 
a fully working implementation that does everything it is supposed to but in addition I added some additional touches
to this assembler like a HD COLOR ASCII graphic duck (my instructors favorite animal) and Blue Screen Of Death when displaying errors.
I hope you enjoy this take on the VC 8000 PDC and with that have a good day 


Assembling the VC 8000 PDC (assuming you are using Visual Studio)

Enable sound

To enable sound right click on the project and select properties
select linker and input click on Additional Dependices and click on the drop down arrow
then click on edit then in the first box type "winmm.lib" (without the quotes) then ok and apply
now sound works in the sense that they are unformatted .wav files but this wasn't even required I wanted to go beyond the minimum requirements

Enable Command line Arguements 

right click on the project and select properties and then click on debugging
and Command Line Arguements select and click on the drop down arrow
then click on edit then in the first box type the name of your file ("Test.txt")

TEST CASES

TEST CASE #1
; file will read in 2 numbers and do a multi register operation on them
        org    100
; read in the 1st number

collin      read    a
; register location(1 in our case) = a
      load 1,a
; save a in the specified register location(1)
      store 1,a
; read in the second number
       read b
; register location(6 in our case) = b
       load 6,b
; save b in the specified register location(6)
       store 6,b
; multiply the 2 registers together 
; you can change this operation code to "addr" for addition "subr" for subtraction
; "multr" for multiplication and "divr" for division (case insensitive)
       MULTR 1,6
; save the resultant in the specified register location
       store 1,a
; a = the resultant
       load 1,a
; display the final answer (a)
       write 1,a
; repeat until the solution is less then or equal to 0
       bp 1,collin

; terminate 
       halt
x      dc      5
y      DS      99
b      dc      555
a      dc      100000000
        end
		
TEST CASE #2

;this is a test
        org    100
hi     read    x;this comment is immediately after statement
        load    1,x
hay   store   1,y ; This is the another comment.
          write    1,x
        bp      1,hi
        halt
    ;test comment
x      dc      5
y      ds      99
b      dc      555
a      dc      100
        end

TEST CASE #3

         org 100
                read 0, n
more        load  1, n; This is a comment

;Here is a comment that sit on its own line.
                mult 1, fac
                store 1, fac
                load 1, n
                sub 1, one
                store 1, n
                bp 0,more
                write 0, fac
                halt
n              ds 100; just to show that you code can handle big areas.
fac           dc 1
one          dc 1
test          dc 1234 ; show your program can handle big constants.
                end