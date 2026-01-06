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







MIPS ASSEMBLY LANGUAGE VERSION- TO USE CODE BELOW, YOU HAVE TO DOWNLOAD: 
1. click download java from https://www.java.com/en/download/
2. click Mars4_5.jar to download from https://github.com/dpetersanderson/MARS/releases/tag/v.4.5.1
3.After you finished download, to start coding, you have to create a new file in MIPS otherwise you won't be able to insert any code in edit section!




