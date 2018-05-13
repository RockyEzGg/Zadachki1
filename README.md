~~~LISP
# Zadachki1
;2 - Определите функцию, возвращающую последни q элемент списка.

(defun last1(lst)
    (cond ((null (cdr lst)) (car lst))
        (t (last1(cdr lst))
    )))


(print (last1 '(a b c d)))

;3 - Определите функцию, заменяющую в исходном списке все вхождения заданного значения другим

(defun change(lst arg value)
    (cond ((null lst) nil)
        ((eq (car lst) arg) (cons value (change (cdr lst) arg value)))
        (t (cons (car lst) (change (cdr lst) arg value )
        
        ))))
       
;15 - Определите функцию, вычисляющую скалярное произведение векторов, заданных списками целых чисел.

(defun multik(vec1 vec2)
    (lambda (x y) (
    (cond ((null (car vec1)) 0)
          ((null (car vec2)) 0)
          (t (+  (* (car vec1) (car vec2)) (multik (cdr vec1) (cdr vec2)) 
          
          ))
          
          )
          ) ((car vec1) (car vec2))
          )
          
;18 - Определите предикат, проверяющий, является ли аргумент одноуровневым списком.

(defun checklist(lst)
    
    (cond ((null lst) t)
          ((atom (car lst)) (checklist (cdr lst)))
          (t nil)
        )
    )
    
;25 - Определите функцию, удаляющую из списка каждый четный элемент.

(defun deleven(lst)
    (cond ((null lst) nil)
          ((null (cdr lst)) lst) 
          (t (cons (car lst) (deleven (cddr lst))))
        )
    )  
    
    
;26 - Определите функцию, разбивающую список (a b с d...) на пары ((а b) (сd)...)

(defun pairs(lst)
    (cond ((null lst) nil)
          (t (cons (list (car lst) (cadr lst)) (pairs (cddr lst)))
     )
    )
    )
  
;28 - Определите функцию, вычисляющую, сколько всего атомов в списке (списочной структуре).

(defun howmany(lst)
    (cond ((null lst) 0)
          ((atom (car lst))(+ 1 (howmany (cdr lst))))
          (t (howmany (cdr lst))) 
        
        )
    )
    
;35 - Определите функцию ПОДМНОЖЕСТВО, которая проверяет, является ли одно множество подмножеством другого.

(defun poisk(a lst)
    (cond ((null lst) nil)
          ((eq a (car lst)) t)
          (t (poisk a (cdr lst)))
        )
    )



(defun subset(a b)
    (cond ((null a) t)
          ((poisk (car a) b) (subset (cdr a) b))
          (t nil)))

;ФВП
;2 - Определите функицонал (MAPLIST fn список) для одного списочного аргумента

(defun maplst(fn lst)
    (cond ((null lst) nil)
          (t (cons (funcall fn (car lst)) (maplst fn (cdr lst))))
         )                 
    )
    
(defun five(arg)
   (cond ((null arg) nil)
          (t 5)
     )
)

;3 Применение каждой функции в списке каждому агрументу списка

(defun apl-apply(f x)
    (mapcar #'(lambda (arg) (mapcar #'(lambda (func) (funcall func arg)) f)) x)   
)










;Макросы

;1. Определите макрос, который возвращает свой вызов. 

(defmacro f (&rest x)
 `(quote (f ,x)))
 (f a b c d)
 
 ;2. Определите макрос (POP стек), который читает из стека верхний элемент и меняет значение переменной стека. 
 
 (defmacro somepop (stack)
  `(let ((first (car ,stack)))(setq ,stack (cdr ,stack))first))
  
 ;3. Определите лисповскую форму (IF условие p q) в виде макроса. 
 
 (defmacro myif (res p q)
    `(if res,p,q))
  (write (myif (> 3 2 )3 2) )
~~~

~~~ Haskell

;;3 - Определите функцию, заменяющую в исходном списке все вхождения заданного значения другим.

rep :: [Integer] -> Integer -> Integer -> [Integer]
rep [] _ _ = []
rep (xh:xt) element value = if element == xh then value:rep xt element value else xh:rep xt element value


;;Выброс нечетных элементов списка

odd :: [Integer] -> [Integer]
odd [] = []
odd (xh:xt) = (head xt) : odd (tail xt)

;;15 - Скалярное произведение векторов

multik :: [Integer] -> [Integer] -> Integer
multik [] []= 0
multik (xh:xt) (yh:yt) = (yh*xh) + (multik xt yt)

~~~

