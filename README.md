import time
seconds = 2
import math




nric = input("Please enter your NRIC, to end program key in q: ")


while nric != "q":
    
    num = nric[1:8]
    nric = nric[0].upper() + nric[1:8] + nric[8].upper()


    while nric[0].isalpha()== False or nric[8].isalpha() == False or nric[1:8].isdigit() == False:
        print("NRIC is unacceptable")
        nric = input("Please re-enter your NRIC: ")
        
    weight = [2,7,6,5,4,3,2]
    weightedsum = 0 
    count = 0

    for i in num:
        weightedsum += int(i) * weight[count]
        count += 1

    total = 0


    if nric[0] == "T" or nric[0] == "G":
        total = weightedsum + 4
        remainder = total % 11
    else:
        total = weightedsum
        remainder = total % 11


    checksum = ""
    if nric[0] == "T" or nric[0] == "S":
        list1 = ["J","Z","I","H","G","F","E","D","C","B","A"]
        checksum = str(list1[remainder])
    else:
        list2 = ["X","W","U","T","R","Q","P","N","M","L","K"]
        checksum = str(list2[remainder])
                    
    correct = ""           
    if checksum == nric[8]:
        correct = "correct"
    else:
        correct = "incorrect"

    
        
        

    print("Weighted Sum is: ",weightedsum)
    
    print("Calculated checksum: ",total)
    
    print("The NRIC number is ",correct )
    for i in range(seconds):
        time.sleep(1)


    nric = input("Please enter your NRIC, to end program key in q: ")
    
print("Program has ended")
