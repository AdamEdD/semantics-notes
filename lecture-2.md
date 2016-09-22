## Programming language design and semantics - cs424 - Barak Pearlmutter

### lecture 2

Scheme - Haskell - Prolog - lambda calculus

**Scheme**
    - simple syntax and semantics

*example:*

    (+ 1 3) ;;;=4
    
*special form:*

    (lamdba ... ) ;;;for defining functions
    
    (lambda (x) (+ x 17) 3) ;;;x=3 -> = 3+17=20
    
*defining functions:*
    
    (define hypot(lambda(x y) (sqrt(+ x y)))) ;;;defines the function hypot
    
*loading files:*

    (load "file.ext")
    
*indenting convention:*

ex1:

    (define myproc
        (lambda(x y)
            (+ x y)))
            
ex2:
    
    (define compose
        (lambda(f g)
            (lambda(x) (f(g x)))))
            
    ;;calling functions:
    
    ((compose 2 3) 100)
    
**if (control statement):**

(if GUARD THEN ELSE)

i.e (if (< 1 2) 1 0) ;;;returns 1 (True)

;;; factorial problem... n! = n*(n=1)!

    (define fact
        (lambda(n)
            (if(= n 1)
                1
                    (*n(fact(- n 1)))))) ;;;recursively called
                    
;;; doesnt work for factorial 0 (diverging - bottom)

;;; fix 0 problem

    ;;;; note that 0! = 1
    
    (define fact
        (lambda(n)
            (if(zero? n) ;;; conditional... zero or n 
                1
                    (*n(fact(- n 1))))))
                    
                    
---------

_partially correct: if the function never returns the wrong answer_

### Binding Variables

you have to create variable functions

(**let** ((var1,val1) (var2,val2) ... (varN,valN)) expression)

you can nest let:

    (let ((x+!)) (let((y (+ x 1))) (+ x (* 100 y)))) ;;; returns 201
    
### Data types

- scheme is not strongly typed (you can mix types)

- strings

- lists

**make a list:**

    (list 2, 17, 34) ;;; returns (2, 17, 34)
    
    (null) or (list) ;;; returns empty list
    
    (cons 3 null) ;;;constructor
    
- get first element from list: 'car'

    (car(list 1 2 3)) ;;; returns 1; index[0] of list
    
- return new list without index[0] (remove first element of list)

    (cdr(list 0 1 2 3 )) ;;; returns (1 2 3)