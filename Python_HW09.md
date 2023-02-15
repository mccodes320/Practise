03. Complete the following program that removes the maximum value from a given list.

![圖片](https://user-images.githubusercontent.com/118010660/219075508-a8ac0caf-0935-41be-a712-c4210ef3ec6f.png)

``` python
values=[17,25,5,30,100,96,48,5,14,30]

#Find the maximun value
largest = values[0]
tmp = 0;
for i in range (0, len(values)):
   if values[i] > largest :
      largest = values[i]
      tmp = i
      print(i , values[i])

# Remove the maxmun value from the list
values.pop(tmp)

print(values)
```

04. Complete the following program that creates a duplicate version of a list but with the elements stored in reverse order from the original.
![圖片](https://user-images.githubusercontent.com/118010660/219075202-c5db610e-42e8-4534-8f4b-7557d122b510.png)


``` python 
origValue = [17,25,5,30,100,96,48,5,14,30]
newValue = []
newValue = [0]*len(origValue)
for i in range (0, len(origValue)) :
  newValue[i] = origValue[len(origValue)-1-i]

print(newValue)
```

05. Implement the fill function that fills all elements of a list with a given value. For example, the call fill(scores, 10) should fill all elements of the list scores with the value 10.

![圖片](https://user-images.githubusercontent.com/118010660/219075027-93f1132b-4abf-4187-8aca-6a5af9b2a1b5.png)

``` python 
def fill(data, value) :
  for i in range (len(data)) :
    data[i] = value
    print(i,data[i])

data = [17,25,5,30,100,96,48,5,14,30]
fill(data,10)
```

pass pass pass

fill( [17, 25, 5, 30, 100, 96, 48, 5, 14, 30] , 10)
[10, 10, 10, 10, 10, 10, 10, 10, 10, 10]
Expected: [10, 10, 10, 10, 10, 10, 10, 10, 10, 10]
fill( [17, 25, 5, 30, 100, 96, 48, 5, 14, 30] , 25)
[25, 25, 25, 25, 25, 25, 25, 25, 25, 25]
Expected: [25, 25, 25, 25, 25, 25, 25, 25, 25, 25]
fill( [8, 6, 9, 3, 5] , 0)
[0, 0, 0, 0, 0]
Expected: [0, 0, 0, 0, 0]


