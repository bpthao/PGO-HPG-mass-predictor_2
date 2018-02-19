# PGO-HPG-mass-predictor_2

f = open('Digest.txt', 'r' )
data = f.readlines()
list_1=[]
list_2 = []
list_3 = []
list_4 = []
list_5 = []

f.close()


for line in data:
    line = line.strip().split()
    list_1.append(float(line[0]))
    list_2.append(line[1])

f1 = open('Modifications.txt', 'r' )
data1 = f1.readlines()
list_3=[]
list_4 = []

for line in data1:
    line = line.strip().split()
    list_4.append(float(line[1]))
    list_3.append(line[0])
    
f_out = open('After_modification.txt', 'w' )
for i in range(len(list_2)):
    a = float(list_2[i].count('R'))
    
    if a >= 1.0:
        for j in range(len(list_4)):
            b1 = float(list_1[i] + list_4[j])
            f_out.write("%f\t%s\t%f\t%s\t\n" % (list_1[i], list_2[i], b1, list_3[j]) )
        
    if a >= 2.0:
        for j in range(len(list_4)):
            for h in range(len(list_4)):
                b11 = float(list_1[i] + list_4[j] + list_4[h])
                
                f_out.write("%f\t%s\t%f\t%s%s\t\n" % (list_1[i], list_2[i], b11,list_3[j], list_3[h]) )
        
    if a >= 3.0:
        for j in range(len(list_4)):
            for h in range(len(list_4)):
                for k in range(len(list_4)):
                    b2 = float(list_1[i] + list_4[j] + list_4[h] + list_4[k])
                
                    f_out.write("%f\t%s\t%f\t%s%s%s\t\n" % (list_1[i],list_2[i],b2,list_3[j],list_3[h],list_3[k]) )
        
f_out.close()
