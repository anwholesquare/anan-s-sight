---
title: "Assembler 8086 Shortcuts"
datePublished: Mon Aug 28 2023 09:06:25 GMT+0000 (Coordinated Universal Time)
cuid: cllunngg5000009l03m9jc9l5
slug: assembler-8086-shortcuts
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693213446091/7e63cbe2-6f73-4f3f-bdf9-fa685ffa1e3e.png
tags: assembly-language, assembler, microprocessors, 8086

---

This article is intended for those with basic knowledge of assemblers and basic ideas of high-level programming languages. To go through the details, we need to download the emu8086 software.

**DOWNLOAD EMU8086**  
[https://emu8086-microprocessor-emulator.en.softonic.com/](https://emu8086-microprocessor-emulator.en.softonic.com/)  
  
**TOPICS WE WILL REVIEW**

1. Registers,
    
2. Template
    
3. I/O,
    
4. Operations,
    
5. Conditions,
    
6. Loop,
    
7. Array,
    
8. Stack
    

1. **REGISTERS**
    
    The 8086 microprocessor, part of the x86 family of processors, has a set of registers that play a crucial role in its operation. These registers store data, addresses, and intermediate results during the execution of instructions. The 8086 assembler registers can be categorized into various types based on their functionality:
    
    1. **General Purpose Registers:**
        
        * AX (Accumulator): This 16-bit register is used for arithmetic and logical operations. It's often used in conjunction with other registers for more complex operations.
            
        * BX (Base): Another 16-bit register that can be used to address memory or as a general-purpose register.
            
        * CX (Count): Often used as a loop counter in string and loop instructions. It can also be used for arithmetic operations.
            
        * DX (Data): This register is used for I/O operations and extended precision arithmetic.
            
    2. **Segment Registers:**
        
        * CS (Code Segment): Points to the start of the code segment in memory.
            
        * DS (Data Segment): Points to the start of the data segment, where variables and data are stored.
            
        * SS (Stack Segment): Points to the stack segment, which is used for storing temporary data during function calls and other operations.
            
        * ES (Extra Segment): An additional segment register that can be used to point to another data segment.
            
    3. **Pointer Registers:**
        
        * SP (Stack Pointer): Points to the top of the stack in the stack segment.
            
        * BP (Base Pointer): Often used to access parameters passed to functions and local variables within stack frames.
            
        * SI (Source Index): Used as an index for string operations.
            
        * DI (Destination Index): Similar to SI, but used as an index for destination data in string operations.
            
    4. **Index Registers:**
        
        * IP (Instruction Pointer): Points to the next instruction to be executed in the code segment.
            
        * Flags Register (FLAGS): Contains various flag bits that reflect the status of previous arithmetic and logic operations. These flags are used for conditional branching.
            
2. **Template**
    
    ```clojure
    .MODEL SMALL
    .STACK 100H
    
    .DATA
    ; ALL DATA MUST BE HERE EXCEPT REGISTERS
    ; DB = DEFINE BYTE | DW = DEFINE WORD 
    MSG DB 'HELLO WORLD $'
    
    .CODE
    MAIN PROC
         ; IT IS A COMMENT
         
         MAIN ENDP
    END MAIN
    ```
    
3. **I/O**
    
    1. **Print "Hello World":**
        
        ```clojure
        .MODEL SMALL
        .STACK 100H
        
        .DATA
        MSG DB 'HELLO WORLD $'
        
        .CODE
        MAIN PROC
             MOV AX, @DATA
             MOV DS, AX
             
             MOV AH, 
             LEA DX, MSG
             INT 21H
             
             MAIN ENDP
        END    
        ```
        
    2. **Read a character and print the character in a new line:**
        
        ```clojure
        .MODEL SMALL
        .STACK 100H
        
        .CODE
        MAIN PROC
            ; Display a character prompt and read a character from the keyboard
            MOV AH, 1       ; Set AH to 1 to indicate "Read Character" function
            INT 21H         ; Call the DOS interrupt to read a character from standard input
            
            MOV BL, AL      ; Store the input character in BL register
            
            ; Display newline character (LF)
            MOV AH, 2       ; Set AH to 2 to indicate "Display Character" function
            MOV DL, 10      ; Set DL to ASCII code 10 (newline character)
            INT 21H         ; Call the DOS interrupt to display the newline character
            
            ; Display carriage return character (CR)
            MOV AH, 2       ; Set AH to 2 again
            MOV DL, 13      ; Set DL to ASCII code 13 (carriage return character)
            INT 21H         ; Call the DOS interrupt to display the carriage return character
            
            ; Display the stored character in BL
            MOV AH, 2       ; Set AH to 2 again
            MOV DL, BL      ; Set DL to the value stored in BL (the input character)
            INT 21H         ; Call the DOS interrupt to display the character
            
            MAIN ENDP
        END
        ```
        
4. **Operations**
    
    ```clojure
    1. SUM:
    ADD AX, BX; AX = AX + BX
    
    2. SUBSTRACT:
    SUB AX, BX; AX = AX - BX
    
    3. MULTIPLY:
    MOV AX, -4
    IMUL BX; AX * BX
    
    4. DIVISION:
    MOV AL, NUM_3 
    MOV BL, 3 
    IDIV BL; AL / BL
    
    5. LOGICAL SHIFT:
    
    ROL AX, 1; ROTATE LEFT FOR THE VALUE OF AX REGISTER
    ROR AX, 1; ROTATE RIGHT FOR THE VALUE OF AX REGISTER
    SHL AX, 1; SHIFT LEFT FOR THE VALUE OF AX REGISTER
    SRL AX, 1; SHIFT RIGHT FOR THE VALUE OF AX REGISTER
    
    6. LOGICAL OPERATION:
    
    AND AX, BX
    OR AX, BX
    NOT AX
    XOR AX, BX
    ```
    
5. **Conditions**
    
    1. **Read two decimal digits and print the largest digit:**
        
    
    ```clojure
    .MODEL SMALL
    .STACK 100H
    
    .DATA
    FIRST DB 'FIRST INPUT: $'
    SECOND DB 'SECOND INPUT: $'
    
    .CODE
    MAIN PROC     
         ; Initialize DS register with the address of the data segment
         MOV AX, @DATA
         MOV DS, AX
         
         ; Display "FIRST INPUT: " prompt
         MOV AH, 9
         LEA DX, FIRST
         INT 21H
         
         ; Read a character from the keyboard
         MOV AH, 1
         INT 21H
         
         ; Store the input character in BL register
         MOV BL, AL 
         
         ; Display newline character
         MOV AH, 2
         MOV DL, 10
         INT 21H
        
         ; Display carriage return character
         MOV AH, 2
         MOV DL, 13
         INT 21H 
         
         ; Display "SECOND INPUT: " prompt
         MOV AH, 9
         LEA DX, SECOND
         INT 21H
         
         ; Read another character from the keyboard
         MOV AH, 1
         INT 21H
         
         ; Store the input character in BH register
         MOV BH, AL 
         
         ; Display newline character
         MOV AH, 2
         MOV DL, 10
         INT 21H
        
         ; Display carriage return character
         MOV AH, 2
         MOV DL, 13
         INT 21H
         
         ; Compare BH and BL, and set DL to the larger of the two
         MOV DL, BH
         CMP BH, BL
         JG PRINT  
         MOV DL, BL
         
         
    PRINT:
         ; Display the value stored in DL (larger of BH and BL)
         MOV AH, 2
         INT 21H
         
            
         MAIN ENDP
    END
    ```
    
    More Jump Instructions  
    1\. JC: Stands for 'Jump if Carry'
    
    2\. JNC: Stands for 'Jump if Not Carry'
    
    3\. JE / JZ: Stands for 'Jump if Equal' or 'Jump if Zero'
    
    4\. JNE / JNZ: Stands for 'Jump if Not Equal' or 'Jump if Not Zero'
    
    5\. JP / JPE: Stands for 'Jump if Parity' or 'Jump if Even Parity'
    
    6\. JNP / JPO: Stands for 'Jump if Not Parity' or 'Jump if Odd Parity'
    
      
    Note: For multi-conditions, we may need to use unconditional jump condition which is ***JMP***  
    
6. **LOOP**
    
    1. **Print “HELLO WORLD” 10 times:**
        
    
    ```clojure
    .MODEL SMALL
    .STACK 100H
    
    .DATA
    MSG DB 'HELLO WORLD $'  ; Define a null-terminated string message
    NEWLINE DB 13,10, '$'   ; Define a newline sequence (carriage return + line feed)
    
    .CODE
    MAIN PROC 
        ; Initialize DS register with the address of the data segment
        MOV AX, @DATA
        MOV DS, AX     
        
        MOV CX, 10       ; Set CX to the number of times to repeat the printing
         
    PRINT:
        ; Display the message
        MOV AH, 9        ; Set AH to 9 to indicate "Display String" function
        LEA DX, MSG      ; Load the address of MSG into DX
        INT 21H          ; Call the DOS interrupt to display the message
        
        ; Display a newline
        MOV AH, 9        ; Set AH to 9 again
        LEA DX, NEWLINE  ; Load the address of NEWLINE into DX
        INT 21H          ; Call the DOS interrupt to display the newline
        
        LOOP PRINT       ; Decrement CX and repeat the loop if CX is not zero
        
    MAIN ENDP
    END
    ```
    
7. **Array**
    
    1. **Read 10 numbers and find the average of the sum:**
        
        ```clojure
        .MODEL SMALL
        .STACK 100H
        
        .DATA
            numbers DB 10 DUP (?)  ; Array to store 10 numbers
            prompt DB 'Enter a number: $'
            newline DB 13, 10, '$'
            avgMsg DB 'Average: $'
            
        .CODE
        MAIN PROC 
            ; Initialize DS register with the address of the data segment
            MOV AX, @DATA
            MOV DS, AX
            
            ; Initialize variables
            MOV CX, 10          ; Set CX to the number of elements
            MOV SI, 0           ; Initialize index for array traversal
            MOV BX, 0           ; Initialize sum
            
        INPUT_LOOP:
            ; Display prompt
            MOV AH, 9
            LEA DX, prompt
            INT 21H
            
            ; Read a number
            MOV AH, 1
            INT 21H
            SUB AL, '0'         ; Convert ASCII character to numerical value
            MOV numbers[SI], AL ; Store the number in the array at index SI
            
            INC SI              ; Move to the next index in the array
            
            LOOP INPUT_LOOP
            
            ; Calculate the sum of the numbers
            MOV CX, 10          ; Reset CX for sum calculation
            MOV SI, 0           ; Reset index for array traversal
            MOV BX, 0           ; Reset sum
            
        SUM_LOOP:
            ADD BL, numbers[SI]
            INC SI
            LOOP SUM_LOOP
            
            ; Calculate the average
            MOV AL, BL
            MOV BL, 10
            DIV BL              ; AL = Sum / 10
            
            ; Display the average
            MOV AH, 9
            LEA DX, avgMsg
            INT 21H
            
            MOV AH, 2
            ADD AL, '0'
            INT 21H
            
            ; Display a newline
            MOV AH, 9
            LEA DX, newline
            INT 21H
            
            ; Exit program
            MOV AH, 4CH
            INT 21H
            
        MAIN ENDP
        END
        ```
        
8. **STACK**
    
    ![](https://faculty.kfupm.edu.sa/COE/shazli/coe205/Help/stack.gif align="center")
    
    1. **Balanced Bracket Problem using PUSH and POP in 8086 assembler:**
        

```clojure
.MODEL SMALL
.STACK 100H

.DATA
    expression DB '(a + [b * {c + d}] - e) $'

.CODE
MAIN PROC
    ; Initialize DS register with the address of the data segment
    MOV AX, @DATA
    MOV DS, AX

    ; Initialize stack pointer
    MOV SP, 100H

    LEA SI, expression

CHECK_LOOP:
    MOV AL, [SI]
    CMP AL, '$'         ; Check for end of expression
    JE EXPRESSION_END

    CMP AL, '('         ; Opening parenthesis
    JE PUSH_STACK
    CMP AL, '['         ; Opening square bracket
    JE PUSH_STACK
    CMP AL, '{'         ; Opening curly brace
    JE PUSH_STACK

    CMP AL, ')'         ; Closing parenthesis
    JE POP_STACK
    CMP AL, ']'         ; Closing square bracket
    JE POP_STACK
    CMP AL, '}'         ; Closing curly brace
    JE POP_STACK

    INC SI              ; Move to the next character
    JMP CHECK_LOOP

PUSH_STACK:
    PUSH AL             ; Push opening bracket onto the stack
    INC SI              ; Move to the next character
    JMP CHECK_LOOP

POP_STACK:
    MOV AH, [SP]        ; Pop bracket from the stack
    CMP AL, '('         ; Matching parenthesis
    JE POP_STACK_DONE
    CMP AL, '['         ; Matching square bracket
    JE POP_STACK_DONE
    CMP AL, '{'         ; Matching curly brace
    JE POP_STACK_DONE

    ; Unmatched brackets, display error message and exit
    MOV AH, 9
    LEA DX, UNMATCHED_MSG
    INT 21H

    ; Exit program
    MOV AH, 4CH
    INT 21H

POP_STACK_DONE:
    ADD SP, 1           ; Pop one element from the stack
    INC SI              ; Move to the next character
    JMP CHECK_LOOP

EXPRESSION_END:
    ; Display balanced expression message
    MOV AH, 9
    LEA DX, BALANCED_MSG
    INT 21H

    ; Exit program
    MOV AH, 4CH
    INT 21H

.DATA
    UNMATCHED_MSG DB 'Unmatched brackets in expression', '$'
    BALANCED_MSG DB 'Expression is balanced', '$'

MAIN ENDP
END
```

# ***To be Continued ...***