# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

    ![image](https://github.com/Darshans05/QRdecomposition/assets/115534676/d6716daf-ed3e-4329-bfb2-1e23ae8665b5)
    ![image](https://github.com/Darshans05/QRdecomposition/assets/115534676/8f7ac2a8-4b77-4f4c-a748-063e1b873114)
    ![image](https://github.com/Darshans05/QRdecomposition/assets/115534676/4e323033-8e46-481b-90f6-64d239091f39)

3.	Obtain the Q matrix   
    ![eqn4](./ex1.jpg)
4.	Construct the upper triangular matrix R
    ![eqn5](./ex2.jpg)



## Program:
### Gram-Schmidt Method
```python
''' 
Program to QR decomposition using the Gram-Schmidt method
Developed by: DARSHAN S 
RegisterNumber: 212222100010
'''
import numpy as np
def QR_Decomposition(A):
    n, m = A.shape
    Q = np.empty((n, n))
    u = np.empty((n, n))
    u[:, 0] = A[:, 0]
    Q[:, 0] = u[:, 0] / np.linalg.norm(u[:, 0])
    for i in range(1,n):
        u[:, i] = A[:, i]
        for j in range(i):
            u[:, i] -= (A[:, i] @ Q[:, j]) * Q[:, j]
        Q[:, i] = u[:, i] / np.linalg.norm(u[:, i])
        
    R = np.zeros((n, m))
    for i in range(n):
        for j in range(i, m):
            R[i, j] = A[:, j] @ Q[:, i]
    print(Q)
    print(R)
a = np.array(eval(input()))
QR_Decomposition(a)
```

## Output
```
![qr decpmposition](https://github.com/Darshans05/QRdecomposition/assets/115534676/328e35cb-145c-4a4e-9067-870f9eaac885)

```

## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
