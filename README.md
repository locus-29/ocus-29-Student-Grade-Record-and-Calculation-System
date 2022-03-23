# Student-Grade-Record-and-Calculation-System

from statistics import mean


# Username & Password List
login_id = {}

# Student List
std_dic = {}


# Home + Function Input
def home(): 
    print('''=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=
    \nWelcome to Grade Central

    [1]-  Enter Gardes
    [2]-  Remove Grades
    [3]-  Remove Student
    [4]-  Add Student 
    [5]-  Average of Students Marks
    [6]-  Total Sum of Students Marks
    [7]-  View Student List & Marks
    [8]-  Exit
    (Type ' 000 ' to escape during any input) \n''')

    choose = input("Choose Number to Continue :  ")
    print("=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=++=+=+=+=+=+=+=+=+=+=+=+=+")


    if choose == "1":              #1
        gradelist()
        for each_student in std_dic:
            grade_list = std_dic[each_student] 
            print("-----------------------------------------------------------------")
            print(each_student ,":- ", grade_list, "\n")
    elif choose == "2":            #2
        rgrade()
        for each_student in std_dic:
            grade_list = std_dic[each_student] 
            print("-----------------------------------------------------------------")
            print(each_student ,":- ", grade_list, "\n")
    elif choose == "3":            #3
        rstd()
        for each_student in std_dic:
            grade_list = std_dic[each_student] 
            print("-----------------------------------------------------------------")
            print(each_student ,":- ", grade_list, "\n")
    elif choose == "4":            #4
        astd()
        for each_student in std_dic:
            grade_list = std_dic[each_student] 
            print("-----------------------------------------------------------------")
            print(each_student ,":- ", grade_list, "\n")
    elif choose == "5":            #5
        avgstd()
    elif choose == "6":            #6
        addstd()
    elif choose == "7":            #7
        for each_student in std_dic:
            grade_list = std_dic[each_student] 
            print("----------------------------------------------------------------")
            print(each_student ,":- ", grade_list, "\n")
    elif choose == "8":            #8
        exit()
    else:                          #9
        print("----------------------------------------------------------------")
        print("Error: Invalid Input")


# Enter Grade System
def gradelist():
    try:
        name = input("\nEnter Name:-  ")
        print("")
        if name == "000":
            home()

        n = int(input("How many subject grades you want to add:- "))

        if n == "000":
            home()
        print("")

        for i in range(n):
            grade = int(input("Enter Grades:-  "))

            if grade == "000":
                break

        
            if name in std_dic:
                print("Adding ",name ,"Grade ....\n")
                std_dic[name].append(int(grade))
            else:
                print("----------------------------------------------------------------")
                print("Error: Invalid Name (name is not present in the saved list)")
                break
    except:
        print("Error: Can't be processed try again")
        gradelist()

# Remove Grade System
def rgrade():
    try:
        name = input("Enter Name:-  ")
        print("")
        if name == "000":
            home()

        nm = int(input("How many Grades you want to remove:- "))
        print("")
        if nm == "000":
            home()
        for i in range(nm):

            grade = int(input("\nEnter Grades:-  ")) 
            if grade == "000":
                break


            if name in std_dic:
                print("Removing the ", name, " grade.....")
                std_dic[name].remove(int(grade))
            else:
                print("Error: Name is not present in the saved list")
                rgrade()
        
    except:
        print("----------------------------------------------------------------")
        print("Error:  Can't be proccessed try again\n")
        rgrade()


# Remove student System
def rstd():

    try:
        nt = int(input("How many students you want to remove:- "))
        print("")
        if nt == "000":
            home()
    

        for i in range(nt):
            name = input("Enter Name:-  ")
            
            if name == "000":
                break

            print ("Removing ", name, " Student....." )
            print("")

            if name in std_dic:
                del std_dic[name]
                
            else:
                print("----------------------------------------------------------------")
                print("Error: Name is not present in the saved list")
                print("")
    except:
        print("Error: Invalid Input")
        rstd()


# Add student system
def astd():

    try:
        nl = int(input("How many students you want to add:- ",))
        print("")
        if nl == "000":
            home()

        for i in range(nl):
            name = str(input("Enter name:-  " ))

            if name == "000":
                break

            x = name.isnumeric()

            if x == True:
                print("Error: Invalid Input")
            else:
                std_dic[name] = []
                print("")
                print("Adding ",name, " in the list.....\n")
        
    except:
        print("Error: Invalid Input")
        astd()


# Login System
def loginsys():

    print("")
    ques = input("Already have an account ?  [ y/n ] :-   ")
    print("")
    
    # already have acoount: 

    if ques == "y" :

        login = str(input("Enter Username:-  "))
        passw = input("Enter Passsword:-  ")


        if login in login_id:
            if login_id[login]== passw:
                print("\nWelcome" , login)
                while True:
                    home()
            else:
                while True:
                    print("----------------------------------------------------------------")
                    print("Error: Invalid Passsword")
                    loginsys()
        else:
            while True:
                print("----------------------------------------------------------------")
                print("Error: Invalid Username")
                loginsys()

    # for creating new account 

    elif ques == "n" :

        k = input("Enter New Username:-  ")
        v = input("Enter New Password:-  ")

        login_id.update({k:v})

        loginsys()

    else:
        while True:
            print("----------------------------------------------------------------")
            print("Error: Invalid Input")
            loginsys()

# Average System
def avgstd():

    try:
        print("Calculating Average........\n")

        for each_student in std_dic:
            grade_list =  std_dic[each_student] 
            avgstd = mean(grade_list)
            print("----------------------------------------------------------------")
            print(each_student ,"has an Average of:- ", avgstd,"\n")
    except:
            print("----------------------------------------------------------------")
            print("Error: Assign marks to all students")

            home()


# Total Sum System
def addstd():
    try:
        print("Adding Marks......\n")

        for each_student in std_dic:
            grade_list =  std_dic[each_student] 
            avgstd = sum(grade_list)
            print("----------------------------------------------------------------")
            print(each_student ,"has an Sum of:- ", avgstd,"\n")
    except:
        print("----------------------------------------------------------------")
        print("Error: Assign marks to all students")
# Output

loginsys()
