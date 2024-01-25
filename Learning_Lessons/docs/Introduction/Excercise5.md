# Excercise 5

## Python Sets Fundamentals

### Simple Demonstration of Sets in Python

Create an empty set:

```python
emptySet = set()
print("Empty Set", emptySet)

setA = {1,2,3,4}
print("set A = ",setA)

setA.add(5)
print("Added Value 5 to set A = ", setA)

setB = {3,4,11,13,15,17}
print("setB = ", setB)

setC = setA.union(setB)
print("Union of Set A and B = ", setC)

setD = setA.intersection(setB)
print("Intersection of Set A and B = ", setD)

caseA = {"Kevin Mitnick", "Jonathon James", "Kevin Poulsen", "Robert Morris"}
caseB = {"Kevin Poulsen", "Robert Morris", "Stephen Wosniak", "Richard Stallman"}
unionCaseAB = caseA.union(caseB)
intersectionCaseAB = caseA.intersection(caseB)

print("Suspects Case A =          ", caseA)
print("Suspects Case B =          ", caseB)
print("Union of Suspects =        ", unionCaseAB)
print("Intersection of Suspects = ", intersectionCaseAB)

print("\nIterate through the union of suspects")
print("notice that the sort order has not changed")

for value in unionCaseAB:
    print(value)

    newList = list(unionCaseAB)
newList.sort()
print(newList)

print("Sorted Set = ", sorted(unionCaseAB))

for value in unionCaseAB:
    print(value)
```



