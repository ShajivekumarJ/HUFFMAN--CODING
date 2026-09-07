# Exp 11 - HUFFMAN--CODING
## Developed By: SHAJIVE KUMAR J 
## Reg N0: 212225230258
## Date: 03/09/2026

## Aim
To implement Huffman coding to compress the data using Python.

## Software Required
1. Anaconda - Python 3.7

## Algorithm:
### Step1: Calculate the frequency of occurrence for each unique character in the given input string.
<br>


### Step2: Construct leaf nodes for every character along with its frequency and store them in a list of nodes.
<br>

### Step3: Sort the list of nodes in ascending order based on their frequencies, then remove the two nodes with the lowest frequencies.
<br>

### Step4: Merge the two smallest nodes to create a new internal node whose frequency is the sum of their frequencies, and add this new node back into the list
<br>

### Step5: Repeat Step 3 and Step 4 recursively until only one combined node (the root of the Huffman tree) remains in the list. Traverse the tree starting from the root—assigning '0' for left branches and '1' for right branches—to generate the binary Huffman code for each character.
<br>

 
## Program:

``` Python
# Get the input String
input_string = "huffman coding"  # Example input string
frequency = {}
for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1

# Create tree nodes
nodes = [[char, freq] for char, freq in frequency.items()]


# Main function to implement huffman coding
while len(nodes) > 1:
    # Sort nodes based on frequency
    nodes = sorted(nodes, key=lambda x: x[1])

    # Pick two smallest nodes
    left = nodes.pop(0)
    right = nodes.pop(0)

    # Create a new node with combined frequency
    new_node = [[left, right], left[1] + right[1]]
    nodes.append(new_node)

# The final node is the Huffman tree
huffman_tree = nodes[0]


# Calculate frequency of occurrence
huffman_codes = {}

def generate_codes(tree, code=""):
    if isinstance(tree[0], str):  # If it's a leaf node
        huffman_codes[tree[0]] = code
    else:  # If it's an internal node, recurse
        generate_codes(tree[0][0], code + "0")
        generate_codes(tree[0][1], code + "1")

generate_codes(huffman_tree)



# Print the characters and its huffmancode
print("Character | Huffman Code")
print("-------------------------")
for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")


```
## Output:

### Print the characters and its huffmancode
<br>
<br>
<img width="252" height="283" alt="image" src="https://github.com/user-attachments/assets/fdb4d6d6-9098-4d49-8d40-4493dbee1f20" />
<br>
<br>



## Result
Thus the huffman coding was implemented to compress the data using python programming.
