# EX-11 Huffman-Coding
### Date:12-11-2024
## Aim
To implement Huffman coding to compress the data using Python.

## Software Required
1. Anaconda - Python 3.7

## Algorithm:
### Step1:
Get the input string
### Step2:
Create tree nodes
### Step3:
Main function to implement huffman coding
### Step4:
calculate frequency of occurence
### Step5:
print the characters and its huffmancode
## Program:
### Get the input String
```python
string = 'DHONI'
class NodeTree(object):
    def __init__(self, left=None, right=None): 
        self.left = left
        self.right=right
    def children(self):
        return (self.left,self.right)
    def nodes (self):
        return (self.left,self.right)
    def __str__(self):
        return '%s %s' %(self.left,self.right)
```
### Create tree nodes
```python
def huffman_code_tree (node, left=True, binString=''):
    if type(node) is str:
        return {node: binString}
    (l, r) = node.children()
    d = dict()
    d.update(huffman_code_tree (l, True, binString + '0'))
    d.update(huffman_code_tree (r, False, binString + '1'))
    return d
```
### Main function to implement huffman coding
```python
freq = {}
for c in string:
    if c in freq:
        freq[c] += 1
    else:
        freq[c] = 1
freq = sorted(freq.items(), key=lambda x: x[1], reverse=True)
nodes=freq
```
### Calculate frequency of occurrence
```python
while len(nodes)>1:
    (key1,c1)=nodes[-1]
    (key2,c2)=nodes[-2]
    nodes = nodes[:-2]
    node = NodeTree (key1, key2)
    nodes.append((node,c1 + c2))
    nodes = sorted (nodes, key=lambda x: x[1], reverse=True)
```
### Print the characters and its huffmancode
```python
huffmanCode=huffman_code_tree(nodes[0][0])
print(' Char | Huffman code ') 
print('----------------------')
for (char, frequency) in freq:
    print('%-4r|%12s'%(char,huffmanCode[char]))
```
## Output:
### Print the characters and its huffmancode
![Screenshot 2024-11-16 194722](https://github.com/user-attachments/assets/cd2b1be9-c50b-4888-afc1-e6b76108c666)
## Result
Thus the huffman coding was implemented to compress the data using python programming.
