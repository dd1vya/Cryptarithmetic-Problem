<h1>ExpNo 8 : Solve Cryptarithmetic Problem,a CSP(Constraint Satisfaction Problem) using Python</h1> 
<h3>Name:DIVYADARSHINI M</h3>
<h3>Register Number:212224060072</h3>

<H3>Aim:</H3>
<p>
    To solve Cryptarithmetic Problem,a CSP(Constraint Satisfaction Problem) using Python
</p>
<h3>Procedure:</h3>
Input and Output
<br>Input:
This algorithm will take three words.
<br> B A S E<br>
    B A L L<br>
           ----------<br>
           G A M E S<br>

Output:
It will show which letter holds which number from 0 – 9.
For this case it is like this.

              B A S E                         2 4 6 1
              B A L L                         2 4 5 5
             ---------                       ---------
            G A M E S                       0 4 9 1 6
Algorithm
For this problem, we will define a node, which contains a letter and its corresponding values.<br>

isValid(nodeList, count, word1, word2, word3)<br>

Input − A list of nodes, the number of elements in the node list and three words.<br>

Output − True if the sum of the value for word1 and word2 is same as word3 value.<br>

Begin<br>
   m := 1<br>
   for each letter i from right to left of word1, do<br>
      ch := word1[i]<br>
      for all elements j in the nodeList, do<br>
         if nodeList[j].letter = ch, then<br>
            break<br>
      done<br>
      val1 := val1 + (m * nodeList[j].value)<br>
      m := m * 10<br>
   done<br>

   m := 1<br>
   for each letter i from right to left of word2, do<br>
      ch := word2[i]<br>
      for all elements j in the nodeList, do<br>
         if nodeList[j].letter = ch, then<br>
            break<br>
      done<br>

      val2 := val2 + (m * nodeList[j].value)
      m := m * 10
   done<br>

   m := 1<br>
   for each letter i from right to left of word3, do<br>
      ch := word3[i]<br>
      for all elements j in the nodeList, do<br>
         if nodeList[j].letter = ch, then<br>
            break<br>
      done<br>

      val3 := val3 + (m * nodeList[j].value)
      m := m * 10
   done<br>

   if val3 = (val1 + val2), then<br>
      return true<br>
   return false<br>
End<br>
<hr>
<h2>Sample Input and Output:</h2>
SEND = 9567<br>
MORE = 1085<br>
<hr>
MONEY = 10652<br>
<hr>

<h3>Program:</h3>

```
import itertools

def solve_cryptarithmetic(addends,result):
    words=addends+[result]
    letters=list(dict.fromkeys("".join(words)))

    if len(letters)>10:
        raise ValueError("Too many letters. Max 10 allowed.")

    lead={w[0] for w in words}

    for p in itertools.permutations(range(10),len(letters)):
        m=dict(zip(letters,p))

        if any(m[x]==0 for x in lead):
            continue

        f=lambda w:int("".join(str(m[c]) for c in w))

        if sum(f(w) for w in addends)==f(result):
            return m

addends=["BASE","BALL"]
result="GAMES"
s=solve_cryptarithmetic(addends,result)

if s:
    print("\nSolution Found:")
    for k in sorted(s):
        print(f"{k} -> {s[k]}")

    print("\nCheck:")
    for i,w in enumerate(addends):
        print(f"{'+ ' if i else ''}{w} ({int(''.join(str(s[c]) for c in w))})")

    print(f"= {result} ({int(''.join(str(s[c]) for c in result))})")

else:
    print("No solution found.")
```
<hr>

<h3>Output:</h3>

<img width="417" height="319" alt="image" src="https://github.com/user-attachments/assets/88bb1183-e4f4-4cba-9898-87d9062567a3" />


<hr>

<h2>Result:</h2>
<p> Thus a Cryptarithmetic Problem was solved using Python successfully</p>
