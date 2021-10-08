# Multiprocessing MatMul, or "Why You Should Always Use NumPy"
I took concurrent.futures, threading, and multiprocessing and built matrix multiplication from integer operations and lists!

## Results
<p float="left", align='center'>
  <b> Vector Dot Product </b> <br>
  <img src="/log_dt_prod_comp.png" width="900" /> <br>
  Comparison of different multiprocessing methods for vector dot product with respect to log-duration
</p>


***
<p float="left", align='center'>
  <b> Matrix Multiply </b> <br>
  <img src="/log_matmul_comp.png" width="800" /> <br>
  Comparison of different multiprocessing methods for vector dot product with respect to log-duration
</p>

We can see that NumPY SIGNIFICANTLY outperformed all the Python multiprocessing functions! This is followed by Python itself, which we attribute to the simplicity of the task and the overhead of actually performing the multiprocessing on the given machine. 

## Why This Project?
I love linear algebra. All the matrix multiplies, inner products, and matricial properties make me happy... really happy. I have also been interested in multiprocessing after a course of distributed computing was offered at my school (which I unfortunately didn't take due to having too many interesting courses that semester). Combining the two seemed like the obvious choice, so here we are. 

### What I did:
First I decided to see how to optimize dot products. I took python, concurrent.futures.ThreadPoolExecutor, concurrent.futures.ProcessPoolExcutor, Threading Thread, and Multiprocessing Pool, and constructed 10 different functions for dot products. I then ran strain tests on all of the functions, realizing that just using numpy was the best, followed by python. I moved on to creating matrix multiplication by picking from the top 5 inner product methods, creating 4 matrix multiplication functions (1 didn't make sense in matrix multiplication). I again ran tests and saw that python by itself was still beating my threaded functions (and numpy knocked everything out of the park). 

## What I did that I didn't like:
1. I wrote the whole project up in a jupyter notebook, but it got crowded really quickly
2. I am not sure I used the threading library to its full potential
3. I tested the code on only one machine - on one with low capabilities, which might explain the results I was getting

## How I would fix the above given another go:
1. Make each function its own .py file, which would clean up the code significantly, and bring them in to the notebook just to run the tests. 
2. Read up more on the threading library and ask for help
3. Use other, potentially more capable, machines to test my code

## Tables

 **Dot Product (5,000 x 1 sized vectors)**


| Method | Time (sec) |
| ------ | ----: |
| Python | 0.0042 |
| concurrent.futures.ThreadPoolExecutor and map | 0.19 |
| concurrent.futures.ThreadPoolExecutor and submit | 0.28 |
| concurrent.futures.ThreadPoolExecutor, submit, and concurrent.futures.as_completed | 0.23 |
| concurrent.futures.ProcessPoolExecutor and map | 2.3 |
| concurrent.futures.ProcessPoolExecutor and submit | 3.2 |
| concurrent.futures.ProcessPoolExecutor, submit, and concurrent.futures.as_completed | 2.2
| Threading.Thread | 0.606 |
| Multiprocessing.Pool and apply | 1.6 |
| Multiprocessing.Pool and apply_async | 1.5 |
| Multiprocessing.Pool and starmap | 0.18 | 
| Multiprocessing.Pool and starmap_async | 0.16 |
| NumPy | 0.00028 |


**Matrix Multiplication (300 x 300 matrices)**
| Method | Time (sec) |
| ------ | ----: |
| Python | 5.8 |
| concurrent.futures.ThreadPoolExecutor and map | 7.2 |
| concurrent.futures.ThreadPoolExecutor and submit |18 |
| Multiprocessing.Pool and starmap | 6.4 | 
| Multiprocessing.Pool and starmap_async | 6.4 |
| NumPy | 0.019 |
