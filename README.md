# a better INPUT
This BASIC V2 code can be used in place of the INPUT command.  It ignores CRSR and HOME keystrokes.  

The standard INPUT command allows the user to move the cursor around the screen with the CRSR up/down, left/right, and HOME keys and even clear the screen. 
This code ignores CRSR, HOME and Function keystrokes on the Commodore 64. All other keystrokes are used to build a string with a length specified by the user. 
Text color is also specified by the user. It could be incorporated as a subroutine into any BASIC program on the C64. Information on the POKES and PEEKS can 
be found in the book, Peeks and Pokes for the Commodore 64 - https://archive.org/details/peeks-and-pokes-for-the-commodore-64, and 
Mapping the Commodore 64 - https://archive.org/details/Compute_s_Mapping_the_Commodore_64

The code is supplied in a d64 image and below

10 co=0:b$="":cc=3:sl=20:bk$=chr$(20)
15 poke 204,1:poke 646,3:poke 647,3:
   poke 204,0
20 if co<sl then poke 198,0:wait 198,1
25 if co=sl goto 70
30 a=peek(203):b=peek(245):c=peek(246)
40 if ((a>=2 and a<=7) or a=51) goto 20
50 if a=1 goto 70
60 if a=0 goto 63
62 goto 66
63 if co>0 then co=co-1:print bk$;:
   b$=left$(b$,co)
64 if co=0 then b$=""
65 goto 15
66 co=co+1
67 d=c*256+b+a:g=peek(d):a$=chr$(g):
   print a$;:b$=b$+a$:goto 15
70 poke 198,0:poke 204,1
80 print" .":print b$
90 end

