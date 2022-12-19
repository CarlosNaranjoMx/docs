## Group by

~~~python
from itertools import groupby
s = input()
#s = "1222311"
result = ""
for i,j in groupby(s):
    sum = 0
    for k in j: 
        sum += 1
    # print(type(i))
    result += "{}".format((sum,int(i)))
    result += " "
print(result[:len(result)])

~~~
## List comprension
~~~python
if __name__ == '__main__':
    x = int(input())
    y = int(input())
    z = int(input())
    n = int(input())

print([[i,j,k] for i in range(x+1) for j in range(y+1) for k in range(z+1) if (i+j+k)!= n ])
~~~
## Runner up
~~~python
if __name__ == '__main__':
    n = int(input())
    arr = map(int, input().split())

mayor = -101
runner_up = -101
for x in arr:
    if x > runner_up and x < mayor:
        runner_up = x
    if x > mayor:
        runner_up = mayor
        mayor = x

print(runner_up)
~~~
## Binary Order
~~~python
debug = 0
def ibinary(list,start,end,elem):
        '''
        :param list: lista que asumimos ordenada
        :param elem: elemento que se agregara a la lista
        '''
        if debug: print("\n")
        if debug: print("iteracion: ",list[start:end],"con:",elem)
        if start==end:
                if debug: print("caso final start: ",start)
                list.insert(start,elem)
                if debug: print("resultado: ",list)
                return list
        if start+1==end: # se inserta en la posicion del end que no se ocupaba
                if debug: print("caso final end: ",end)
                list.insert(end,elem)
                if debug: print("resultado: ",list)
                return list
        # mitad piso
        # (0+1)//2 = 0
        # (0+2)//2 = 1
        # (0+3)//2 = 1
        half_dif = (end-start)//2
        half_2 = half_dif+start
        if debug: print("(start,half_2,end):",start,half_2,end)
        half_elem= list[half_2]
        if half_elem>=elem:
                if debug: print(elem,"es mas chico que",half_elem," entonces:",list[start:half_2],start,half_2)
                ibinary(list,start,half_2,elem)
        if half_elem<elem: 
                if debug: print(elem," es mas grande que", half_elem,"entonces: ",list[half_2:end],half_2,end)
                ibinary(list,half_2,end,elem)
# el final como un elemento menos que el inicio
ibinary([],0,0,'a')
ibinary(["a","c","d",'e',"h"],0,5,"f")

if debug : print("ingrese el rango")
for _ in range(int(input())):
        name = input()
        # print(name)
        score = float(input())
        # print(score)
~~~

## Finding the percentage

~~~python
from functools import reduce

if __name__ == '__main__':
    n = int(input())
    student_marks = {}
    for _ in range(n):
        name, *line = input().split()
        scores = list(map(float, line))
        student_marks[name] = scores
    query_name = input()

lista = student_marks[query_name]
lista_len = len(lista)
suma = reduce(lambda a,b:a+b,lista)
print('{:.2f}'.format(suma/lista_len))
~~~