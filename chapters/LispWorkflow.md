# Lisp workflow

Install:

```bash
apt-get install screen
```


```lisp
(defun count-occurs (x y)
  (cond ((equalp x y) 1)
	((atom y) 0)
	((endp y) 0)
	((+
	  (count-occurs x (car y))
	  (count-occurs x (cdr y))))
	)
  )
```


Bye.
