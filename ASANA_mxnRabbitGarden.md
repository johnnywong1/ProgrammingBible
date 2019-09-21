# ASANA's MxN Rabbit Garden Problem.

Given an NxM matrix representing a garden, each entry  contains a number,which is the number of carrots in that plot.
A rabbit starts in the middle,or plot closest to middle with the most carrots and always goes up down leftor right
after eating to the plot with the most carrots. No negative entries,write some code that given a garden matrix, you 
return the number of carrotsa rabbit would eat in it. No IDE's, no compiling/running code, no looking stuff up,appropriate
to copy answer from text editor. Had to click an honor code.One hour timed limit from acceptance of a link.

```
import math


test = [[5, 7, 8, 6],
         [0, 0, 7, 0],
         [4, 6, 3, 4],
         [3, 1, 0, 5]]

def findCenter(inputMatrix):
  # Calculate center first
  length, width = len(inputMatrix), len(inputMatrix[0])
  centL = centW = potL = potW = 0
  if length % 2 == 1:
    centL = math.ceil(length/2)
  else:
    potL = [length//2 -1, length//2 ]

  if width % 2 == 1:
    centW = math.ceil(width/2)
  else:
    potW = [width//2 -1, width//2]

  if centL and centW:
    return [centL, centW]
  else:
    if not centL and not centW:
      testCases = [[l,w] for w in potW for l in potL]
      print(testCases)  
    elif not centL:
      testCases = [[l,centW] for l in potL]
    else: # not centW:
      testCases = [[centL,w] for w in potW]

  # Grab the index of the "testcenter" with the highest carrot
  testValues = [inputMatrix[e[0]][e[1]] for e in testCases]
  retVal = testCases[testValues.index(max(testValues))]
  # print(retVal)
  return retVal

# I realized too late that I don't really need a dictionary of traversed,
# can just replace val with 0
# I want to do a recursive jump essentially through the garden
def moveRabbit(inputMatrix, point):
  retValue = inputMatrix[point[0]][point[1]]
  inputMatrix[point[0]][point[1]] = 0

  left = [point[0], point[1]-1]
  right = [point[0], point[1]+1]
  up = [point[0]-1, point[1]]
  down = [point[0]+1, point[1]]
  potDirec = [ dir for dir in [left,right,up,down] if dir[0] >=0 and dir[1] >= 0]

  bestValue = [inputMatrix[e[0]][e[1]] for e in potDirec]

  if max(bestValue) == 0:
    return retValue

  best = potDirec[bestValue.index(max(bestValue))]
  return retValue + moveRabbit(inputMatrix, best)

  

x =moveRabbit(test, findCenter(test))
print(x)
# print(moveRabbit(test, findCenter(test)))
```
