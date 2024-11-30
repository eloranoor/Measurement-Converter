.MODEL SMALL
.STACK 100H
.DATA

inp db 2 dup('$')
count db ?

chose db ?
con db ?
str1 db "                            Measurement Converter$"
cf db "1. Celsius, Fahrenheit$"
mc db "2. Meter, Centimeter$"
ck db "3. Celsius, Kelvin$"
yf db "4. Yard, Feet$"

ctof db "1. Celsius to Fahrenheit$"
ftoc db "2. Fahrenheit to Celsius$"
mtocm db "1. Meter to Centimeter$"
cmtom db "2. Centimeter to Meter$"
ctok db "1. Celsius to Kelvin$"
ktoc db "2. Kelvin to Celsius$"
ytof db "1. Yard to Feet$"
ftoy db "2. Feet to Yard$"

a db "Please choose one: $"

cel db "Enter a Celsius Value: $"
fah db "Enter a Fahrenheit Value: $"
m db "Enter a Meter Value: $"
cm db "Enter a Centimeter Value: $"
kel db "Enter a Kelvin Value: $"
yardd db "Enter a Yard Value: $"
feett db "Enter a Feet Value: $"

outcel db "Equivalent Celsius Value: $"
outfah db "Equivalent Fahrenheit Value: $"
outcm db "Equivalent Centimeter Value: $"
outm db "Equivalent Meter Value: $"
outk db "Equivalent Kelvin Value: $"
outf db "Equivalent Feet Value: $"
outy db "Equivalent Yard Value: $"


cel_val dw ?
fah_val dw ?
m_val dw ?
cm_val dw ?
celsius db ?
kelvin  dw 0
kelvinn db ?
celsiuss dw 0

inte db ?
flt db ?
tripval1 db ?
tripval2 db ?

quo_1000 dw ?
rem_1000 dw ?
quo_100 dw ?
rem_100 dw ?
quo_10 dw ?
rem_10 dw ?
cmm dw ?
mm dw ?

f db 00H

id dw 00H
c dw 0
b dw 0

quo db ?
rem db ?

ff dw 00H
g db 00h

yard db ?
fet db ?
fpfeet db 00h
yardrem db ?

feet db ?
convert db 3
fr db ?
tripfeet1 db ?
tripfeet2 db ?
tripans dw ?

.CODE

MAIN PROC

MOV AX, @DATA
MOV DS, AX


mov ah, 9
lea dx, str1
int 21h

mov ah, 2
mov dl, 0Dh
Int 21h
mov dl, 0Ah
int 21h

mov ah, 2
mov dl, 0Dh
Int 21h
mov dl, 0Ah
int 21h
;==============

mov ah, 9
lea dx, cf
int 21h

mov ah, 2
mov dl, 0Dh
Int 21h
mov dl, 0Ah
int 21h

mov ah, 9
lea dx, mc
int 21h

mov ah, 2
mov dl, 0Dh
Int 21h
mov dl, 0Ah
int 21h

mov ah, 9
lea dx, ck
int 21h

mov ah, 2
mov dl, 0Dh
Int 21h
mov dl, 0Ah
int 21h

mov ah, 9
lea dx, yf
int 21h

mov ah, 2
mov dl, 0Dh
Int 21h
mov dl, 0Ah
int 21h

mov ah, 9
lea dx, a
int 21h

mov ah, 1
int 21h
sub al, 30h
mov chose, al

mov ah, 2
mov dl, 0Dh
Int 21h
mov dl, 0Ah
int 21h

;============

cmp chose, 01h
je dcf

cmp chose, 02h
je dmcm

cmp chose, 03h
je dck

cmp chose, 04h
je dyf

dcf:
mov ah, 9
lea dx, ctof
int 21h

mov ah, 2
mov dl, 0Dh
Int 21h
mov dl, 0Ah
int 21h

mov ah, 9
lea dx, ftoc
int 21h

mov ah, 2
mov dl, 0Dh
Int 21h
mov dl, 0Ah
int 21h
jmp here

dmcm:
mov ah, 9
lea dx, mtocm
int 21h

mov ah, 2
mov dl, 0Dh
Int 21h
mov dl, 0Ah
int 21h

mov ah, 9
lea dx, cmtom
int 21h

mov ah, 2
mov dl, 0Dh
Int 21h
mov dl, 0Ah
int 21h

jmp here

dck:
mov ah, 9
lea dx, ctok
int 21h

mov ah, 2
mov dl, 0Dh
Int 21h
mov dl, 0Ah
int 21h

mov ah, 9
lea dx, ktoc
int 21h

mov ah, 2
mov dl, 0Dh
Int 21h
mov dl, 0Ah
int 21h

jmp here

dyf:
mov ah, 9
lea dx, ytof
int 21h

mov ah, 2
mov dl, 0Dh
Int 21h
mov dl, 0Ah
int 21h

mov ah, 9
lea dx, ftoy
int 21h

mov ah, 2
mov dl, 0Dh
Int 21h
mov dl, 0Ah
int 21h
here:
mov ah, 9
lea dx, a
int 21h

mov ah, 1
int 21h
sub al, 30h
mov con, al

mov ah, 2
mov dl, 0Dh
Int 21h
mov dl, 0Ah
int 21h
;===============
cmp chose, 01h
je pcf

cmp chose, 02h
je pmcm

cmp chose, 03h
je pck

cmp chose, 04h
je pyf

pcf:
cmp con, 01h
je pcel ;celtofah

cmp con, 02h
je pfah ;fahtocel
pmcm:
cmp con, 01h
je pm ;mtocm

cmp con, 02h
je pcm ;cmtom
pck:
cmp con, 01h
je pcels;celtokel

cmp con, 02h
je pkel ;keltocel
pyf:
cmp con, 01h
je pyard ;yardtofeet

cmp con, 02h
je pfeet  ;feettoyard

pcel:
mov ah, 9
lea dx, cel
int 21h
jmp taking_input

pfah:
mov ah, 9
lea dx, fah
int 21h

jmp taking_input

pm:
mov ah, 9
lea dx, m
int 21h

jmp taking_input

pcm:
mov ah, 9
lea dx, cm
int 21h

jmp taking_input

pcels:
mov ah, 9
lea dx, cel
int 21h
jmp taking_input

pkel:
mov ah, 9
lea dx, kel
int 21h
jmp taking_input

pyard:
mov ah, 9
lea dx, yardd
int 21h
jmp taking_input

pfeet:
mov ah, 9
lea dx, feett
int 21h
jmp taking_input

;=============================================display===================================================

;==============================================input=====================================================
;taking input from user
taking_input:
mov si, 0
mov cx, 2
;user can take upto 2 values|(xx or x, NOT .x)

mov ah,1

input:
int 21h
cmp al, 13 ;if user press enter, it will stop taking input
je conversion

sub al, 30h
mov inp[si], al

mov bl, al
mov bh, 0
push bx

inc si
inc count
loop input



;========================================input=========================================================

;=======================================conversion====================================================

conversion:  ; will compare based on what user has given, then will go to conversion

mov ah, 2
mov dl, 0Dh
Int 21h
mov dl, 0Ah
int 21h

cmp chose, 01h
je cpcf

cmp chose, 02h
je cpmcm

cmp chose, 03h
je cpck

cmp chose, 04h
je cpyf


cpcf:
cmp con, 01h
je convcel

cmp con, 02h
je convfeh
cpmcm:
cmp con, 01h
je convm

cmp con, 02h
je convcm
cpck:
cmp con, 01h
je convcels

cmp con, 02h
je convkel

cpyf:
cmp con, 01h
je convyard

cmp con, 02h
je convfeet

;=====================================Celsius to Fahrenheit Conversion===================================================

convcel:


MOV ax,00H
CMP count,1
je onecel

mov al, inp[0]  ;two input
mov bl,10
mul bl
add al,inp[1]
jmp conti_cel

onecel:
add al,inp[0]    ;one input


conti_cel:


mov ah, 0                ;f= c*9/5 +32
mov bl, 9
mul bl


mov bl, 5
mov dx, 0
div bl

add al, 32

mov inte, al
mov flt, ah


jmp output


jmp exit
;========================================Fahrenheit to Celcius Conversion=========================================================
convfeh:
MOV ax,00H
CMP count,1
je sing
mov al, inp[0]      ;two input
mov bl,10
mul bl
add al,inp[1]
jmp pa
sing:
add al,inp[0]       ;one input
pa:
CMP al,32
jl flag
jmp continue
flag:
mov f,1             ;for neg values

continue:
mov ah, 0
mov bl, 32
mov bh,0
;c = f-32 * 5/9
sub ax, bx

cmp f,1
je negv
jmp notneg
negv:
neg ax                ;for easier calculation, shift the value into a positive value

notneg:
mov bl, 5
mul bl

mov bl, 9
div bl

mov inte, al
mov flt, ah

jmp output

;========================================Meter to Centimeter Conversion=========================================================
convm:

MOV ax,00H

CMP count,1
je onee         ;if input given is just 1  digit

mov al, inp[0]
mov bl,10
mul bl
add al,inp[1]   ;making 2 digit number
jmp continuee

onee:           ;1 digit number
add al,inp[0]



continuee:      ;conversion

mov bl,100
mul bl          ;Multiply with 100 [examples: 1200d==04b0h   200d==0C8h]
mov inte,al     ;inte holds val of al, for 1200d=b0h & 200d==C8h
mov flt,ah      ;flt holds val of ah, for 1200d==04h   200d==00h
jmp output

;========================================Centimeter to Meter Conversion=========================================================
convcm:

MOV ax,00H

CMP count,1      ;if input given is just 1  digit
je oneee

mov al, inp[0]
mov bl,10
mul bl
add al,inp[1]    ;making 2 digit number
mov cmm,ax       ;inputting number in cmm
jmp continueee

oneee:
add al,inp[0]
mov cmm,ax        ;1 digit number


continueee:
mov ah, 0
mov dx,0
mov bl,100
div bx
mov quo_100, ax   ;quotient in al, 0
mov rem_100,dx    ;reminder in dl, 78


jmp output

;========================================Celsius to Kelvin Conversion==============================
convcels:
cmp count,1 ; WHEN GIVEN INPUT IS 1
je one
mov SI,id
MOV Al,inp[SI] ; takeing value from array to al
MOV bl,0AH
MUL Bl ; mul 10
MOV celsius,Al
inc id

one:
mov SI,id
MOV BL,inp[SI]
Add celsius,bl

MOV AH, 0

MOV AL, celsius ; store the celsius val in al
ADD AX, 273  ; add 273 for convertion

MOV kelvin, AX ; store the value in kelvin
MOV BX,kelvin
MOV c,BX
jmp output
;;=========================================Kelvin to Celsius Conversion;=========================================

convkel:
cmp count,1 ; when the input is 1 digit
je two

;for double input
mov si,id
mov al,inp[si] ; taking val from array to al
mov bl,0ah
mul bl    ; mul al= 10*al
mov kelvinn,al
inc id
two:
mov si,id
mov bl,inp[si]
add kelvinn,bl


MOV Al, kelvinn
mov ah, 0
SUB AX, 273 ; add 273 to the input val for convertion
neg ax  ; making it to negative
MOV celsiuss, Ax ; storing the negative val to celsiuss
mov ah,0
jmp output
;=========================================Yard to Feet Conversion=======================================

convyard:
MOV ax,00H
CMP count,1
je onefeet



mov al, inp[0]  ;two input  ;13
mov bl,10                       ;1
mul bl                      ;10
add al,inp[1]                ;3 = 10+3 = 13
jmp  cont

onefeet:
add al,inp[0] ; 1 val input in al

cont:
MOV bl, convert; 3 for multiply
mov bh,0
mul bx  ; AX = AX * BX
mov feet, al ; Store output into feet
mov fr, ah ; for input 86 and up

jmp output






;=========================================Feet to Yard Conversion==================================
convfeet:

MOV ax,00H
CMP count,1
je onefeett

mov al, inp[0]  ;two input  ;1
mov bl,10
mul bl                      ;10
add al,inp[1]                ;3 = 10+3 = 13
jmp conti_feet

onefeett:
add al,inp[0]    ;one input

conti_feet:

mov ah, 0
mov cx,3  ; for  1,2,0
cmp ax,cx
jl fracpart


mov bl, 3 ; 2 digit input
div bl    ; al= al/3


mov yard, al ; quotient
mov yardrem, ah  ; reminder
jmp output

fracpart:                ;0,1, 2
mov bl, 3
div bl  ; al=al/bl , ah= reminder(0,1,2)

mov rem, ah ; store the reminder to rem
inc fpfeet  ; counter to see if the number is 0,1,2
jmp output




;=============================================ALL OUTPUTS=========================================================
output:

cmp chose, 01h
je opcf

cmp chose, 02h
je opmcm

cmp chose, 03h
je opck

cmp chose, 04h
je opyf

opcf:
cmp con, 01h
je ofah

cmp con, 02h
je ocel
opmcm:
cmp con, 01h
je ocm

cmp con, 02h
je om
opck:
cmp con, 01h
je okel
cmp con,02h
je celso

opyf:
cmp con, 01h
je ofeet

cmp con, 02h
je oyard


;========================================Celcius to Fahrenheit Output============================================
ofah:
mov ah, 9
lea dx, outfah
int 21h
cmp inte, 64h ; for  100+ values
jge tripcel
cmp inte, 0h ; for signed decimal minus value
jl tripcel

cmp inte, 0Ah
jge doublecel

mov ah, 2
mov dl, inte       ;one value
add dl, 030h
int 21h
jmp fltcel

doublecel:            ;double value
mov al, inte
mov ah, 0
mov bl, 0Ah      ;12/10 = 1 in al, 2 in ah
div bl

mov bh, ah
mov ah, 2
mov dl, al
add dl, 30h
int 21h
mov dl, bh
add dl, 30h
int 21h

jmp fltcel

tripcel:
mov al, inte        ;210
mov ah, 0
mov bl, 10
div bl

mov tripval1, ah   ;third val= 0

mov bl, 10
mov ah, 0
div bl

mov tripval2, ah     ;second val= 1

mov ah, 2
mov dl, al    ;first val =2
add dl, 30h
int 21h

mov ah, 2
mov dl, tripval2
add dl, 30h
int 21h

mov ah, 2
mov dl, tripval1
add dl, 30h
int 21h

fltcel:
mov dl, '.'
mov ah, 2
int 21h

mov al, flt
cmp al, 1
je p2

cmp al, 6
je p2

cmp al, 2
je p4

cmp al, 7
je p4

cmp al, 3
je p6

cmp al, 8
je p6

cmp al, 4
je p8

cmp al, 9
je p8

mov ah, 2
mov dl, 30h
int 21h
jmp exit


p8:
mov ah, 2
mov dl, 38h
int 21h
jmp exit
p6:
mov ah, 2
mov dl, 36h
int 21h
jmp exit
p4:
mov ah, 2
mov dl, 34h
int 21h
jmp exit
p2:
mov ah, 2
mov dl, 32h
int 21h
jmp exit


;========================================Fahrenheit to Celcius Output=========================================================
ocel:
mov ah, 9
lea dx, outcel
int 21h

cmp f,1
je minus
jmp normal
minus: ; for 32 and less input values
mov ah, 2
mov dl, '-'
int 21h
normal:

cmp inte,0AH
jge double

mov ah,2
mov dl,inte
add dl,030h
int 21h
jmp fltt
double:
mov al,inte
mov ah,0
mov bl,0AH
div bl
mov bh,ah
mov ah,2
mov dl, al
add dl, 30h
int 21h
mov dl, bh
add dl, 30h
int 21h

fltt:
mov dl, '.'
mov ah, 2
int 21h

mov ah, 2
mov dl, flt
add dl, 30h
int 21h

jmp exit
;========================================Meter to Centimeter Output=========================================================

ocm:


jmp normall



normall:

mov ah, 9
lea dx, outcm
int 21h

cmp count,2
je two_num

mov al,inte  ;1 digit number
mov ah,flt
mov mm,ax
jmp work

two_num:
mov ax,0
mov al,inte
mov ah,flt
mov mm, ax    ;2 digit number

work:
cmp mm,1000
jg doublee


mov dx,0       ;if input 1 digit[cm=200]
mov ax,mm
mov cx,100
div cx
mov quo_10,ax   ;quo_10=2
mov rem_10,dx   ;rem_10=00

mov ah,2
mov dx,quo_10   ;2
add dl,30h
int 21h


mov cx,2
zeroo_print:    ;00
mov ah,2
mov dl,30h
int 21h
loop zeroo_print
jmp exit



doublee:            ;if input is 2 digits[1200]
mov ax,mm
mov cx,1000
mov dx,0
div cx
mov quo_1000,ax     ;1000_quo=1
mov rem_1000,dx     ;1000_rem=200

mov cl,30h
add dl,30h
cmp dl,cl           ;[0!=200]
jne div_100

mov ah,2
mov dx,quo_1000
add dl,30h          ; 1
int 21h

mov cx,3
zero_print:
mov ah,2
mov dl,30h
int 21h
loop zero_print
jmp exit



div_100:
mov ax,rem_1000     ;200
mov cx,100


mov dx,0
div cx
mov quo_100,ax      ;100_quo=2
mov rem_100,dx      ;100_rem=00

mov cl,30h
add dl,30h
cmp dl,cl           ;[if20!=0 ]
jne div_10

mov ah,2
mov dx,quo_1000
add dl,30h          ; 1
int 21h

mov ah,2
mov dx,quo_100
add dl,30h          ; 2
int 21h

mov cx,2
zerooo_print:       ; 00
mov ah,2
mov dl,30h
int 21h
loop zerooo_print
jmp exit


;10

div_10:
mov ax,rem_100
mov cx,10


mov dx,0
div cx              ;20/10
mov quo_10,ax       ;10_quo=2
mov rem_10,dx       ;10_rem=0



mov ah,2
mov dx,quo_1000
add dl,30h         ; 1
int 21h

mov ah,2
mov dx,quo_100
add dl,30h         ; 2
int 21h


mov ah,2
mov dx,quo_10
add dl,30h         ; 2
int 21h

mov ah,2
mov dx,rem_10
add dl,30h         ; 0
int 21h

jmp exit

;========================================Centimeter to Meter Output=========================================================

om:

jmp normalll



normalll:
mov ah, 9
lea dx, outm
int 21h

mov ax,cmm      ;78 or 4eh

mov cx,100
cmp ax,cx
jl deci_print   ;<100 so decimal

;else print 100

mov ah,2
mov dl,1
add dl,30h
int 21h

mov ah,2
mov dl,0
add dl,30h
int 21h

mov ah,2
mov dl,0
add dl,30h
int 21h

deci_print:

mov ah,2
mov dl,30h
int 21h   ;prints 0

mov ah,2
mov dl,02Eh
int 21h   ;prints '.'

cmp count,2
je two_numm

;1 digit input:
mov ah,2
mov dl,30h
int 21h   ; 0

mov ah,2
mov dx,rem_100
add dl,30h       ;8
int 21h

jmp exit

two_numm: ;2 digit input
mov ax,rem_100 ;4eh
mov cx,10  ;A
mov dx,0
div cx ;al=7,dl=8
mov quo_10,ax
mov rem_10,dx



mov ah,2
mov dx,quo_10
add dl,30h     ;7
int 21h

mov ah,2
mov dx,rem_10
add dl,30h       ;8
int 21h

jmp exit


;========================Celsius to Kelvin Output==========================

okel:
mov ah, 9
lea dx, outk
int 21h

;cmp kelvin,999
;                        jg digit4
cmp kelvin,99
jg digit3



; digit4:
;                        MOV CX, 4 ; assuming a 4-digit result
;                        MOV BX, 10 ; divisor for decimal conversion
;                        MOV AX, kelvin
;                        DigitLoop:
;                        MOV Ax, c  ; celsius val store in ax
;                        mov dx, 00h
;                        DIV Bx
;                        mov b,dx ; reminder store in b
;                        add b,30h
;                        mov c, ax
;                        mov dh,0
;                        mov dx,b ; reminder storen dx
;                        push dx
;                        loop DigitLoop
;                        mov cx,4
;                        print:
;                        pop dx
;                        mov ah,02h
;                        int 21h
;                        loop print
;                        jmp exit

digit3:
mov cx,3
mov bx,10
DigitLoop1:
MOV AX, c ; celsius val store in ax  285
mov DX, 00h
DIV Bx  ; 285/10=al=28
mov b,DX  ; reminder store in b=5
add b,30h
mov c, ax ; 28
mov dx,b  ; reminder storen dx=5
push dx ; 5 push
loop DigitLoop1
mov cx,3
print1:
pop dx  ; 285
mov ah,02h
int 21h
loop print1
jmp exit
;===================================Kelvin to Celsius Output==============================
celso:
mov ah, 9
lea dx, outcel
int 21h

MOV Ah,2
MOV Dl,'-'
INT 21H

mov cx,3

MOV AX,celsiuss; celsiuss value in ax =176
MOV DX,00H
MOV BX,0AH ; moving 10
DIV BX  ; ax=176/10=17
MOV ff,DX ; reminder store in dx =6
MOV DX,00H
DIV BX ;17/10=1=al
MOV g,Dl ; reminder value store=7

MOV Ah,2
MOV DL,Al ; quotient=1
add dl,030H
INT 21H  ;print 1
MOV Dl,g ; reminder in al for print  =7
add dl,030H
INT 21H
MOV Dx,ff ; reminder 6
add dx,030H
INt 21H
jmp exit

;====================================Yard to Feet Output==================================

ofeet:
mov ah, 9
lea dx, outf
int 21h
cmp count,1
je single

cmp feet, 64h  ; for 100 up values after mul
jge tripfeet
cmp feet, 0   ;for signed decimal minus  values after mul
jl tripfeet
cmp fr, 0    ; if after mul the value is upto 255
jg tripfeet86
cmp feet,0AH ; more than 10
jge doubley
single:
mov ah,2

cmp feet, 10
jge td ; single input like 4,5,6,7,8,9
mov dl,feet
add dl,30h
int 21h
jmp exit

td:
mov bl, 10
mov al, feet ; 27
mov ah, 0
div bl ;27/10=2

mov rem, ah ;7
mov ah, 0
mov bl,0AH
div bl  ;2/10=0
mov ch,ah ;rem 2 pass
mov ah, 2
mov dl,ch ;2 print
add dl,30h
int 21h
mov ah, 2
mov dl, rem ;7
add dl, 30h
int 21h
jmp exit


doubley:
mov al,feet
mov ah,0
mov bl,0AH
div bl
mov bh,ah  ; rem in bh
mov ah,2
mov dl, al
add dl, 30h
int 21h ; al print
mov dl, bh
add dl, 30h
int 21h  ; rem print

jmp exit

tripfeet:
mov al, feet  ;125
mov ah, 0
mov bl, 10
div bl    ; al=125/10 ; rem in ah

mov tripfeet1, ah; 5 store in  tripfeet1

mov bl, 10 ; 12/10=al
mov ah, 0
div bl

mov tripfeet2, ah  ;rem 2

mov ah, 2
mov dl, al ; 1st val print=1
add dl, 30h
int 21h

mov ah, 2
mov dl, tripfeet2 ; remder 2 print
add dl, 30h
int 21h

mov ah, 2
mov dl, tripfeet1 ; print 5
add dl, 30h
int 21h

jmp exit   ;input 85


tripfeet86:        ;86 and up


mov ah, fr   ; 258 , ah=2=fr
mov al, feet ; 58= feet
mov tripans, ax ;whole value saved

; same thing as tripfeet
mov ax, tripans

mov bl, 10
div bl

mov tripfeet1, ah

mov bl, 10
mov ah, 0
div bl

mov tripfeet2, ah

mov ah, 2
mov dl, al
add dl, 30h
int 21h

mov ah, 2
mov dl, tripfeet2
add dl, 30h
int 21h

mov ah, 2
mov dl, tripfeet1
add dl, 30h
int 21h

jmp exit



;====================================Feet to Yard Output============================
oyard:
mov ah, 9
lea dx, outf
int 21h

cmp fpfeet, 1 ;for inputs 0,1,2 fpfeet=1
je fraco
cmp yard, 0Ah      ;10<
jge doublef

mov ah, 2
mov dl, yard   ;1
add dl, 30h
int 21h
jmp pprint

doublef:
mov al, yard ;34
mov ah, 0
mov bl, 0Ah
div bl    ; 34/10=al=3=quo

mov bh, ah ; bh=rem=ah=4

; for 3 print
mov ah, 2
mov dl, al ;quo=al=dl=3
add dl, 30h
int 21h
; for 4 print
mov dl, bh
add dl, 30h ;bh=dl=4
int 21h

pprint:
mov ah, 2
mov dl, 02Eh  ; print '.'
int 21h

mov ax,0


cmp yardrem, 1       ;hex/rem 1, 4, 7 =.3
je pr3

cmp yardrem, 4
je pr3

cmp yardrem, 7
je pr3

cmp yardrem, 2         ;hex/rem 2, 5,8 = .6
je pr6

cmp yardrem, 5
je pr6

cmp yardrem, 8
je pr6


mov ah, 2  ; print 0
mov dl, 30h
int 21h
jmp exit


pr3:
mov ah, 2
mov dl, 33h ; print 3
int 21h
jmp exit
pr6:
mov ah, 2
mov dl, 36h ; print 6
int 21h
jmp exit



jmp exit


fraco:            ;input 0,1,2

mov ah, 2
mov dl, 0          ; print 0
add dl, 30h
int 21h

mov ah, 2
mov dl, 02Eh        ;print '.'
int 21h

mov ax,0
mov al,rem          ;rem=1
mov cl,10
mul cl              ;rem val *10 =al


mov dl,3
div dl               ;quo 3(al) rem 1(ah)
mov quo,al           ;quo=3
mov rem,ah           ;rem=1

mov cl,ah
cmp cl,0  ;seeing if reminder 0 or not
jne f_pri

;else print 1 digit after point

mov ah, 2
mov dl, quo
add dl, 30h
int 21h

jmp exit

f_pri:
mov ah, 2
mov dl, quo   ;quo=3
add dl, 30h
int 21h

mov al,rem
mov cl,10     ;rem=1
mul cl ;10

mov dl,3
div dl         ;quo 3(al) rem 1(ah)



mov ah,2
mov dl,al     ;quo al=3
add dl,30h
int 21h
jmp exit


; YOUR CODE ENDS HERE
exit:
MOV AH, 4CH
INT 21H

MAIN ENDP
END MAIN




; [SOURCE]: C:\Users\elora\Desktop\341 project\Group 3_Measurement Conversion_Sec07.asm
