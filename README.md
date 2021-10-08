# Multiprocessing MatMul, or Why You Should Always Use NumPy
I took concurrent.futures, threading, and multiprocessing and built matrix multiplication from integer operations and lists!

## Why?
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
