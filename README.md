# easuBadge

def activation_func(a):
    if a>0:
        return 1
    elif a==0:
        return 0
    else:
        return -1
ans=[]
/////////
data=[[0,0],[0,1],[1,0],[1,1]]
labels=[0, 1, 1, 1]
learning_rate=1
b=0.0
weight=[0.0,0.0]
epochs=50
///////
for epoch in range(epochs):
    print(f"epoch count:{epoch+1}")
    res=[]
    for ip,target in zip(data,labels):
        weighted_sum=(weight[0]*ip[0])+(weight[1]*ip[1])+b
        pred=activation_func(weighted_sum)
        error=target-pred
        res.append(pred)
        weight[0]+=learning_rate*error*ip[0]
        weight[1]+=learning_rate*error*ip[1]
        b+=learning_rate*error
        if error!=0.0:
            print(f"Error between target and prediction: {error}")
            print(f"Updated weight:\n weight1: {weight[0]}\n weight2: {weight[1]}")
            print(f"Updated bias:{b}")
    print(f"After epoch({epoch+1}): {res}")
    ans=res
    if labels==ans:
        print("Lables matched after epoch cycle: ",epoch+1)
        break
if labels!=ans:
    print("Results have mismatched output")
