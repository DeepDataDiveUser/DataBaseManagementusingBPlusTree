# B+ Tree
Implementing B+ tree using C++
- [x] Search 
- [X] Insert
- [ ] Delete
- [ ] Structuring the main Function
- [ ] Adding animations (AddOn)


##Some UseFul Properties of B+ Tree:
1. B+ Tree Unlike B Tree is defined by two order values one for leaf node and another for non-leaf node.
	Minimum 50% should hold on B+ Tree Node.
	a.	For Non-Leaf Nodes-
		i.	ceil(maxInternalLimit)<= #of children <= maxInternalLimit
		ii.	ceil(maxInternalLimit)-1<= #of keys <= maxInternalLimit-1
		
	b.	For Leaf Nodes-
		i.	ceil(maxLeafLimit)<= #of children <= maxLeafLimit
		ii.	ceil(maxLeafLimit)-1<= #of keys <= maxLeafLimit-1	

	[B+	TreeBasics](img/prop_1.png)



##Insertion:

There are two convention being followed for the insertion(according to the google what i found out)
where, if the current node becomes full then -

1.	First give an element to the left sibling and if that doesn't
work give an element to the right sibling and if this also doesn't work split it.

2.	Simply Split into two nodes.

We have followed 2nd method which was comparatively easy to implement with relatively less hustle. So, 
here is the complete algorithm for [reference](http://www.cburch.com/cs/340/reading/btree/index.html?fbclid=IwAR0QFRcpIVL19PdMtZU0-wG18f-rwGS4lNvzpEAsdaZCL7BrNRBuFffiPJ0)

Descend to the leaf node where leaf fits :
a.	If the node has empty space, insert the key/reference pair into the node.
b.	If the node is already full, split it into two nodes, distributing the keys evenly. 
	i.	If the node is leaf,take the copy of minimum in the second node and repeat this algorithm to 
		insert it in parent node.
	ii.	If the node is non-leaf, exclude the middle value during split and insert the excluded value into 
		the	parent.


