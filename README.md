# RoundRobinAlgorithm
 def lcm(x,y):
    if x>y:
        lcm_=x
    else:
        lcm_=y
    while(True):
        if((lcm_%x==0)and(lcm_%y==0)):
            break
        lcm_+=1
        
    return lcm_
 
def WatitingTime(n,bt,wt,q,v,lcm):
     rem=bt.copy()
     finished=0
     t=0
     while (finished!=n):
         for j in range(lcm):
              
             for i in range (n):
                if(t<j):
                    t+=1
                if(v[i]<=j):
                    if rem[i]>0:
                       
                       if rem[i]>q:
                          
                           t+=q
                           rem[i]-=q
                          
                       
                       else:
                         
                           t=t+rem[i]
                           wt[i]=t-v[i]-bt[i]
                              
                           rem[i]=0
                           finished+=1
            
                        
                             
                 
                       
                             
                             
        
         
                    

def TurnAroundTime(n,bt,wt,tat):
    
    for i in range(n):
        t=bt[i]+wt[i]
        tat[i]+=t
        
        
 
                    
def findtime(pro,n,tat,wt):
    totaltat=0
    totalwt=0
    for i in range(n):
        totalwt=totalwt+wt[i]
        totaltat=totaltat+tat[i]
    print('Average Waiting time='+str(totalwt/n))
    print('Average Turn around time=' +str(totaltat/n))
    
     
 
 
def Display(n,burst,wt,tat,v):
    print('Processes'+'  Arrival time'+'  Burst Time'+'  Waiting Time'+'  Turn Around Time'+'\n')
    for i in range(n):
        
     print(' '+str(pro[i])+'\t\t\t\t'+str(v[i])+'\t\t\t\t'+str(burst[i])+'\t\t\t\t'+str(wt[i])+'\t\t\t\t'+str(tat[i]))
 
bt=[0,0]
bt[0]=int(input('please enter  Execution1: '))
bt[1]=int(input('please enter  Execution2: '))
pro=[11,21]
n=2
wt=[0,0]
tat=[0,0]
 
m=0
num1=11
num2=21
x=int(input('please enter Period1: '))
 
y=int(input('please enter  Period2: '))
q=int(input('please enter  Quantum: '))
lcm=lcm(x,y)
v=[0,0]
ba=0
for i in range(lcm):
  if(i>2):
    if(i%y==0):
        n=n+1
        num2+=1
        wt.append(m)
        tat.append(m)
        pro.append(num2)
        v.append(i)
        bt.append(bt[1])
     
    elif(i%x==0):
        n=n+1
        num1+=1
        wt.append(m)
        tat.append(m)
        pro.append(num1)
        v.append(i)
        bt.append(bt[0])
        
for i in range(n):
    ba=ba+bt[i]
          
w=10
e=100/lcm 
bahre=e*ba       
print( 'n:'+str(n))
 
WatitingTime(n,bt, wt,q,v,lcm )
TurnAroundTime( n, bt, wt, tat)
Display(n, bt, wt, tat, v) 
findtime( pro, n, tat, wt)
print('Efficiency='+str(bahre))
