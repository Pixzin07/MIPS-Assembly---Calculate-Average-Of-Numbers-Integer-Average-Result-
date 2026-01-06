
PYTHON VERSION SO YOU CAN UNDERSTAND MIPS ASSEMBLY EASIER!! 

    def main():
    totals = 0
    count = 0
    control = True
    
    while control:
        value = int(input("Please enter a number with range 0-100 (-1 to stop): "))

        if value == -1:
            print("I won't bother you anymore for the sake of peace")
            control = False
        elif value < 0 or value > 100:
            print("You're out of range sir/ma'am/they")
        else:
            totals += value
            count += 1

    if count > 0:
        average = totals // count
    else:
        average = 0

    print("Average:", average)
    main()





MIPS ASSEMBLY LANGUAGE VERSION- TO USE CODE BELOW, YOU HAVE TO DOWNLOAD OR GO TO RELEASE FILES AND DOWNLOADED IT THERE!!
1. click download java from https://www.java.com/en/download/
2. click Mars4_5.jar to download from https://github.com/dpetersanderson/MARS/releases/tag/v.4.5.1
3.After you finished download, to start coding, you have to create a new file in MIPS otherwise you won't be able to insert any code in edit section!



Link brief explaination(Youtube): https://youtu.be/4mtt4-FPVxM

    .data
    prompt:      .asciiz "Please enter a number with range 0-100 (-1 to stop): "
    errorMsg:    .asciiz "You're out of range sir/ma'am/they\n"
    stopMsg:     .asciiz "I won't bother you anymore for the sake of peace\n"
    averageMsg:  .asciiz "Average: "

    .text
    .globl main

    main:
        li $t0, 0          # totals = 0
        li $t1, 0          # count = 0
        li $t2, 1          # control = True (1)

    input_loop:
        beq $t2, $zero, done_input   # if control == 0, exit loop
    
        # print prompt
        li $v0, 4
        la $a0, prompt
        syscall

        # read integer
        li $v0, 5
        syscall
        move $t3, $v0      # values = input

        # check if input == -1
        li $t4, -1
        beq $t3, $t4, stop_input

        # check if 0 <= values <= 100
        blt $t3, 0, invalid_input
        bgt $t3, 100, invalid_input

        # valid input: totals += values, count += 1
        add $t0, $t0, $t3
        addi $t1, $t1, 1
        j input_loop

    invalid_input:
        li $v0, 4
        la $a0, errorMsg
        syscall
        j input_loop

    stop_input:
        # print stop message
        li $v0, 4
        la $a0, stopMsg
        syscall

        li $t2, 0          # control = False
        j input_loop

    done_input:
        # check if count > 0
        beqz $t1, no_input

        # average = totals / count (integer division)
        div $t5,$t0, $t1   # average in $t5    
        #alternative way to store $t5    
        #mflo $t5    
        j print_average
    
    no_input:
        li $t5, 0          # if no input, average = 0
    
    print_average:
        # print "Average: "
        li $v0, 4
        la $a0, averageMsg
        syscall
    
        # print integer average
        move $a0, $t5
        li $v0, 1
        syscall
    
        li $v0, 10         # exit
        syscall
