
/////////////////////////////////////////////////////////////////
///                        README.txt                         ///
/////////////////////////////////////////////////////////////////

Author:  Jason W Gould
Program: Forward Chaining - Tic Tac Toe!

Tested on Python version: 2.7.6

================================================================
===                   FILES REQUIRED TO RUN                  ===
================================================================

1. fc.py        (Python Program)
2. ttt.kb       (Knowledge base) 

================================================================
===                       INSTRUCTIONS:                      ===
================================================================

1.  This program uses forward chaining to suggest the next best possible
    move. It works by applying the forward chaining algorithm and the user
    input board state to the knowledge base I defined in ttt.kb

2.  To use the forward chaining program, simply run 
    fc.py with the knowledge base and board state:

EX STATE:      
    |_O_|___|___| 
    |_O_|___|_X_| 
    |_X_|___|___| 

INPUT:
    > python fc.py ttt.kb "o11 b12 b13 o21 b22 x23 x31 b32 b33 turn_x"

OUTPUT:
    ...
    move_x13_setup

3.  Included files: 
    - Sample program traces and output of example board states:
        trace1.txt, trace2.txt, trace3.txt, trace4.txt
    - Four test states:
        trace5.txt, trace6.txt, trace7.txt, trace8.txt
    - The program:
        fc.py
    - The knowledge base:
        ttt.kb

================================================================
===                       Analisis                           ===
================================================================
Analisis forward chaining pada program tic-tac-toe solver

program ini berfungsi untuk merekomendasikan langkah terbaik pada giliran berikutnya. 
menggunakan forward chaining untuk merekomendasikan langkah berdasarkan state yang ada, terdapat 3 parameter yaitu o, x , dan b.
contoh state :

    | _ O _ | _ _ _ | _ _ _ | 
    
    | _ O _ | _ _ _ | _ X _ | 
    
    | _ X _ | _ _ _ | _ _ _ | 

untuk blank area dimasukan sebagai b, o sebagai o dan x sebagai x
contoh penggunaan program jika berdasarkan state diatas maka
perintah : python fc.py ttt.kb "o11 b12 b13 o21 b22 x23 x31 b32 b33 turn_x"
output : move_x13_setup

karena tidak adanya kemungkinan menang maka program merekomendasikan untuk langkah setup

contoh state jika kondisi memungkinkan menang

    | _ O _ | _ _ _ | _ X _ | 
    
    | _ O _ | _ X _ | _ X _ | 
    
    | _ _ _ | _ _ _ | _ _ _ | 

perintah : python fc.py ttt.kb "o11 b12 x13 o21 x22 x23 b31 b32 b33 turn_o"
output : move_o31_can_win

contoh state jika lawan mempunyai kemungkinan menang

    | _ O _ | _ _ _ | _ _ _ | 
    
    | _ O _ | _ X _ | _ X _ | 
    
    | _ _ _ | _ _ _ | _ _ _ | 
    
perintah : python fc.py ttt.kb "o11 b12 b13 o21 x22 x23 b31 b32 b33 turn_o"
output : move_x31_forced

algoritma program:

jika kondisi tidak mempunyai kemungkinan menang baik pemain maupun lawan maka akan merekomendasikan untuk langkah setup
jika kondisi mempunyai kemungkinan menang untuk pemain selanjutnya maka akan merekomendasikan langkah menang
jika kondisi mempunyai kemungkinan lawan untuk menang maka akan merekomendasikan langkah memblock


