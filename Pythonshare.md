# Python
Predicting share price of a company using it's profit
import csv
with open('data3.csv', newline='') as csvfile:
    data = list(csv.reader(csvfile))
i=0
s=0
share=[]
profit=[]
n=15
diff_year=0.0
for i in range(1,n):
    profit.append(float(data[i][2]))
    share.append(float(data[i][1]))
def menu():
    print("MAIN MENU")
    print("1: Show data")
    print("2: Central tendency and standard deviation values of profit and share")
    print("3: Regression")
    print("4:correlation")
    print("5: Prediction")
    print("6: Hypothesis")
    print("7:Graph")
    print("8:Quit")
    choice=int(input("Enter your choice:"))
    while True:
        if choice==1:
            showdata()
            menu()
        elif choice==2:
            centraltendency()
            menu()
        elif choice==3:
            reg()
            menu()
        elif choice==4:
            corr()
            menu()
        elif choice==5:
            prediction()
            menu()
        elif choice==6:
            hypothesis()
            menu()
        elif choice==7:
            graph()
            menu()
        elif choice==8:
            print("Thank You!!!")
            exit(1)
        else:
            print("You must only select either 1,2,3,4,5,6,70r8.")
            print("Please try again")
            menu()
def showdata():
    i=0
    x.field_names = [data[0][0], data[0][1], data[0][2]]
    for i in range (1,15):
        x.add_row([data[i][0], data[i][1], data[i][2]])
    print(x)#Printing data in a table using PrettyTable
def centraltendency():
    #Calculating Mean ,median and mode
    mean=np.mean(profit)
    median=np.median(profit)
    mode=stats.mode(profit)
    mean1=np.mean(share)
    median1=np.median(share)
    mode1=stats.mode(share)
    s=statistics.stdev(profit)
    s1=statistics.stdev(share)
    print("Mean of profit:",mean)
    print("Median of profit:",median)
    print("Mode of profit:",mode)
    print("Mean of share:",mean1)
    print("Median of share:",median1)
    print("Mode of share:",mode1)
    print("standard deviation of profit",s)
    print("standard deviation of shares",s1)
    print("********************************")
def corr():
    corr=np.corrcoef(profit,share)
    print("correlation:",corr)
    if(corr.all()>0):
        print("increase in profit increases share")
    else:
        print("increse in profit decreases share")
    if(corr.all()>0.2 and corr.any()<0.5):
        print("low correlation")
    elif(corr.any()==0.5):
        print("moderate correlation")
    elif(corr.any()>0.5):
        print("high correlation")
    print("**************************")
def reg():
    cov=0.0
    mx=0.0
    my=0.0
    mx2=0.0
    b=0.0
    a=0.0
    mx=np.mean(profit)
    my=np.mean(share)
    for i in range(len(profit)):
        cov=cov+((profit[i]-mx)*(share[i]-my))
        mx2=mx2+((profit[i]-mx)**2)
        b=cov/mx2
        a=my-b*mx
    print("y = {} + {}x".format(a,b))
    print("*****************************")
def prediction():
   cov1=0.0
   mx1=0.0
   my1=0.0
   mx3=0.0
   b1=0.0
   a1=0.0
   y=0.0
   mx1=np.mean(profit)
   my1=np.mean(share)
   for i in range(len(profit)):
       cov1=cov1+((profit[i]-mx1)*(share[i]-my1))
       mx3=mx3+((profit[i]-mx1)**2)
       b1=cov1/mx3
       a1=my1-b1*mx1
   ye=int(input("Enter the year :"))
   y=a1+b1*ye
   print("The predicted shares of the year {} is {}".format(ye,y))
   print("***********************************************")
