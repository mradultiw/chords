
# Ropes
##### Height Balanced Threaded Rope Data Structure
```bash
pip install pyropes
```
```bash
Author: Mradul Tiwari
Tester: Self
Documentation: Self
language: Python 3.7.4
Purpose: Education
Date created: 27 June, 2020
OS used: Windows 10 Home
```
## Credits
Following Sources are used, with modifications, for making this project successful. I acknowledge and am grateful to these developers.
- Test Suite: The test suite used for final testing belongs to ***Marshall Ward*** ([https://github.com/marshallward](https://github.com/marshallward))
- Display API: As answered by ***J. V.*** on stack overflow (https://stackoverflow.com/a/54074933)

## About

This Documentation shows use cases of "**Height Balanced Threaded Rope Data Structure**".
Ropes are mutable data structures for string processing. Operations like split, insert, delete, are performed in time O(logn) in Ropes, unlike conventional strings which have O(n) time complexity. Concatenation is done in O(1) in Ropes( O(logn) with threads & balancing). However accessing value at an index is O(logn) in ropes while O(1) in conventional strings.
This implementation of Ropes is ***"Height Balanced With Threads"***. Motivation of height balancing has been taken from **AVL Trees** and **Threads** are attached to all leaf nodes to make traversal fast, the motivation of which came from **Threaded Binary Trees**.
  
The purpose of this library is to help students(or any learner) to learn about ropes, height balancing, threading in trees, writing and maintaining large python code and all of this can be visualised as well (yes! the tree that you draw on paper) which makes it easy to track what's happening in the code.
## Functionalities and Usage
### Constructors

>- Rope() -> new empty Rope object.
>- Rope(string, leafsize=4) -> Create a Rope from string with leafsize=4 , (default leafsize is 8)
>- Rope([string1, string2, string3]) -> Equivalent to Rope(string1 + string2 + string3)
*Any container can be used above but should have string type elements
### Detailed examples
```python
>>> from pyropes import Rope
>>> raw = "This_is_a_test_string_for_Rope_DataStructure"
>>> rope1 = Rope(raw)
>>> rope2 = Rope(raw, leafsize = 12)
>>> rope1, rope2
```
```
(Rope('This_is_a_test_string_for_Rope_DataStructure'),
 Rope('This_is_a_test_string_for_Rope_DataStructure'))
```
```python
>>> rope1.display()
```
```
                     ___________________(22)____________________                    
                    /                                           \                   
          ________(11)_________                       ________(11)_________         
         /                     \                     /                     \        
     ___(6)___             ___(6)___             ___(6)___             ___(6)___    
    /         \           /         \           /         \           /         \   
(This_i)   (s_a_t)    (est_st)   (ring_)    (for_Ro)   (pe_Da)    (taStru)   (cture)
```
```python
>>> rope2.display()
```
```
                ______________(22)_______________               
               /                                 \              
       ______(11)______                  ______(11)______       
      /                \                /                \      
(This_is_a_t)    (est_string_)    (for_Rope_Da)    (taStructure)
```
```python
>>> raw = ["Thi","s_is","_a_test","_stri","ng_for","_Rope_Data","Str", "ucture"]
>>> rope1= Rope(raw)
>>> rope2 = Rope(raw, leafsize = 10)
>>> rope1.display()
>>> rope1
```
```
                        ___________________(25)___________________                  
                       /                                          \                 
           __________(14)________                       ________(10)______          
          /                      \                     /                  \         
     ____(7)____             ___(5)____            ___(5)___           __(3)____    
    /           \           /          \          /         \         /         \   
(This_is)   (_a_test)    (_stri)   (ng_for)    (_Rope)   (_Data)    (Str)   (ucture)

Rope('This_is_a_test_string_for_Rope_DataStructure')
```
```python
>>> rope2.display()
>>> rope2
```
```
                        ________(19)_________________________             
                       /                                     \            
           __________(14)___                  _____________(16)_____      
          /                 \                /                      \     
     ____(7)____         (_stri)         ___(6)______          (Structure)
    /           \                       /            \                    
(This_is)   (_a_test)               (ng_for)   (_Rope_Data)              

Rope('This_is_a_test_string_for_Rope_DataStructure')
```
```python
>>> (rope1[1],rope2[1]), (rope1[2:5],rope2[2:5])
```
```
((Rope('h'), Rope('h')), (Rope('is_'), Rope('is_')))
```
```python
>>> rope1[:8],rope2[:8]
```
```
(Rope('This_is_'), Rope('This_is_'))
```
```python
>>> rope2.display()
```
```
            ___________________(19)_________________________             
           /                                                \            
      ____(8)_________                       _____________(16)_____      
     /                \                     /                      \     
(This_is_)        ___(6)___             ___(6)______          (Structure)
                 /         \           /            \                    
             (a_test)   (_stri)    (ng_for)   (_Rope_Data)               
```
```python
>>> rope1[ : : 2]
```
```
Rope('Ti_sats_tigfrRp_aatutr')
```
```python
>>> rope1==rope2, rope1 is rope2
```
>Ropes are considered equal if they represent same string.
```
(True, False)
```
```python
>>> rope3 = rope1.copy()
>>> rope1==rope3, rope1 is rope3
```
```
(True, False)
```
```python
>>> new = rope1.append( rope2 )
>>> rope1, new, rope1 == new, rope1 is new 
```
>Note: rope2 is sharing memory with rope1(or new) so any change made in rope2 will be reflected in rope1. To overcome this, use '+' operator instead
```
(Rope('This_is_a_test_string_for_Rope_DataStructureThis_is_a_test_string_for_Rope_DataStructure'),
 Rope('This_is_a_test_string_for_Rope_DataStructureThis_is_a_test_string_for_Rope_DataStructure'),
 True,
 True)
```

##### > Now let's see some more operations but on some smaller strings which can fit easily on screen
```python
>>> rope1 = Rope('abcde', leafsize = 3)
>>> rope1, print(rope1)
```
```
abcde

(Rope('abcde'), None)
```
```python
>>> rope2 = rope1 + Rope("_I'm a ROPE")
>>> rope1, rope2, rope1 is rope2
```
>Note: here, rope2 is NOT SHARING memory with any of rope1 or Rope("_I'm a ROPE"). Alwasys,'+'  returns a copy of Rope on Right side
```
(Rope('abcde'), Rope('abcde_I'm a ROPE'), False)
```
```python
>>> rope3 = rope1 + "_I'm a string"
>>> rope1, rope3, rope1 is rope3
```
>type(rope3) is also Rope despite of concatnating string as operand

```
(Rope('abcde'), Rope('abcde_I'm a string'), False)
```
```python
>>> rope4 = rope1 * 3
>>> rope1, rope4, rope1>rope4
```
```
(Rope('abcde'), Rope('abcdeabcdeabcde'), False)
```
 ```python                  
>>> rope1[ 2 ] = '*'
>>> rope4[ 4 ] = '#'
>>> rope1, rope4
```
>clearly shows that rope1 and rope1*4 are NOT SHARING any memory. 
>Note: index based slicing do NOT update rope structure

```
(Rope('ab*de'), Rope('abcd#abcdeabcde'))
```

```python
>>> show = lambda x : f"( { x.val if x.val else x.weight }, { x.height } )"
```
>'show' will governs what will Rope.display() shows 
```python
>>> rope1 = Rope("abcdefghi", leafsize = 3)
>>> rope1, rope1.display(show)
```
```
          ________(5,2)________         
         /                     \        
    ___(3,1)___            __(2,1)___   
   /           \          /          \  
(abc,0)     (de,0)     (fg,0)     (hi,0)

(Rope('abcdefghi'), None)
```
```python
>>> rope1[ 2 : 5 ] = "_I'M_INSERTED_"
>>> rope1, rope1.display(show)
```
>Each internal node will show (weight,height) while leaves showing (value,height)

```
                                           ___________________(13,4)_________                    
                                          /                                  \                   
                    ____________________(9,3)________                   ___(3,2)________         
                   /                                 \                 /                \        
         ________(4,2)________                   __(2,1)___         (ED_,0)         __(2,1)___   
        /                     \                 /          \                       /          \  
    __(2,1)___            __(2,1)___         (SE,0)     (RT,0)                  (fg,0)     (hi,0)
   /          \          /          \                                                            
(ab,0)     (_I,0)     ('M,0)     (_IN,0)            
                                             
(Rope('ab_I'M_INSERTED_fghi'), None)
```
```python
>>> rope1.leafsize=5
>>> rope1.display(show)
```
> changing leafsize will implicitly calls rope.refresh()
```
                         __________(13,3)_________           
                        /                         \          
           ___________(9,2)____              ___(3,1)____    
          /                    \            /            \   
     ___(4,1)____          (SERT,0)      (ED_,0)     (fghi,0)
    /            \                                           
(ab_I,0)     ('M_IN,0)
```
```python
>>> rope=Rope( [ "This ", "Rope_will", " be splitted in" ] ) + "_to_two_parts"
>>> rope, rope.display()
```
```
         _________________(14)________________________                      
        /                                             \                     
    ___(5)________                        __________(15)__________          
   /              \                      /                        \         
(This )       ___(5)___             ____(8)____              ____(7)____    
             /         \           /           \            /           \   
          (Rope_)   (will)    ( be spli)   (tted in)    (_to_two)   (_parts)
          
(Rope('This Rope_will be splitted in_to_two_parts'), None)
```
```python
>>> left_rope, right_rope = rope.split(18)
>>> left_rope, left_rope.display()
```
```
         ________(10)_____     
        /                 \    
    ___(5)___        (will be )
   /         \                 
(This )   (Rope_)        
      
(Rope('This Rope_will be '), None)
```
```python
>>> right_rope, right_rope.display()
```
```
        __________(11)__________          
       /                        \         
    __(4)____              ____(7)____    
   /         \            /           \   
(spli)   (tted in)    (_to_two)   (_parts)

(Rope('splitted in_to_two_parts'), None)
```
```python
>>> left_rope == rope, left_rope is rope
```
>shows that left_rope and rope are pointing to same rope

```
(True, True)
```
#### > A Rope object can also be initialised empty. See below:
```python
>>> rope1 = Rope(leafsize = 5)
>>> rope1, rope1.display()
```
```
(Rope(''), '')
```
```python
>>> rope1 = rope1 + "I_am_added_to_empty_rope"
>>> rope1, rope1.display()
```
```
               ______________(12)______________               
              /                                \              
       ______(6)______                  ______(6)______       
      /               \                /               \      
   __(3)__         __(3)__          __(3)__         __(3)__   
  /       \       /       \        /       \       /       \  
(I_a)   (m_a)   (dde)   (d_t)    (o_e)   (mpt)   (y_r)   (ope)

(Rope('I_am_added_to_empty_rope'), None)
```
```python
>>> rope1.delete(2)
>>> rope1, rope1.display()
```
```
         ______________(11)______________               
        /                                \              
    ___(5)______                  ______(6)______       
   /            \                /               \      
(I_m_a)      __(3)__          __(3)__         __(3)__   
            /       \        /       \       /       \  
          (dde)   (d_t)    (o_e)   (mpt)   (y_r)   (ope)
          
(Rope('I_m_added_to_empty_rope'), None)
```
```python
>>> rope2 = rope1.delete(3,11)
>>> rope1, rope1.display()
```
```
       ________(8)______       
      /                 \      
   __(3)___          __(3)__   
  /        \        /       \  
(I_m)   (_empt)   (y_r)   (ope)

(Rope('I_m_empty_rope'), None)
```
```python
>>> rope2, rope2.display()
```
```
    ___(5)___   
   /         \  
(_adde)   (d_to)

(Rope('_added_to'), None)
```
```python
>>> rope2[0:0] = "Added_IN_FRONT"
>>> rope2, rope1
```
>Look that memory isn't shared between deleted rope and remaining rope
```
Rope('Added_IN_FRONT_added_to'), Rope('I_m_empty_rope'))
```
```python
>>> rope2.reverse()
>>> rope2, rope2.display()
```
```
        ________(9)_______________                
       /                           \               
    __(4)___               _______(7)______        
   /        \             /                \       
(ot_d)   (edda_)       __(3)___         __(3)___   
                      /        \       /        \  
                    (TNO)   (RF_N)   (I_d)   (eddA)

(Rope('ot_dedda_TNORF_NI_deddA'), None)
```
```python
>>> rope2.reverse()   #To bring original after previous rope2.reverse()
>>> rope2.split_merge(5,13,11)
>>> rope2, rope2.display()
```

>split_merge(i,j,k) will extract rope from [i:j] (both inclusive) and insert it before kth index in remaining Rope
```
                    ______(13)_______________       
                   /                         \      
         ________(10)__               ______(7)__   
        /              \             /           \  
    ___(5)___        (d_I)        __(4)__      (_to)
   /         \                   /       \          
(Added)   (_adde)             (N_FR)   (ONT)        

(Rope('Added_added_IN_FRONT_to'), None)
```

#### > Now some common operation on strings (more operations will be released in future)  
```python
>>> rope1 = Rope("ABcdefGh").lower()
>>> rope2 = Rope("ABcdefGh").upper()
>>> rope3 = Rope("ABcdefGh").swapcase()
>>> rope4 = Rope("ABcdefGh").capitalize()
>>> rope1, rope2, rope3, rope4
```          
```
(Rope('abcdefgh'), Rope('ABCDEFGH'), Rope('abCDEFgH'), Rope('Abcdefgh'))
```
              
```python
>>> (rope1.islower(),rope1.isupper()), (rope2.islower(),rope2.isupper())
```
```((True, False), (False, True))```

```python
>>> rope1 = Rope("AbcdEF23h")
>>> rope1.isalnum(), rope1.isalpha(), rope1.isascii()
```
```(True, False, True)```
```python
>>> rope1.isdecimal(), Rope("123").isdecimal()
```
```(False, True)```
---
There are still a lot of functionalities and usages but I encourage you to go through all functions available and read their doc strings to know more about them.

### Final Words: 
Although I've taken every care while creating Ropes and writing this documentation, despite if you find any bug, report it.
Any suggestions to improve code/documentation are heartily welcomed.
