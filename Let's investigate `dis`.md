---
theme: black
transition: none
controls: "false"
timeForPresentation: "300"
---

Riddle me this! 🐍

<split even gap="1">

```python
>>>  a = {}
>>>  a = a[0] = {}
>>>  print(a)
 ```

```python
>>>  b = {}
>>>  b[0] = b = {}
>>>  print(b)
```
</split>

---

Riddle me this! 🐍

<split even gap="1">

```python
>>>  a = {}
>>>  a = a[0] = {}
>>>  print(a)

a={0: {...}}
 ```

```python
>>>  b = {}
>>>  b[0] = b = {}
>>>  print(b)

b={}
```
</split>

---

<split even gap="1">

```python
a = a[0] = {}
```

~

```python
temp = {}
a, a[0] = (temp, temp)
```
</split>
---
Let's investigate `dis`!

---

`from dis import dis`

---

```python
>>>  dis("""  
...    a = a[0] = {}  
...  """)

2     0 BUILD_MAP                0
	  2 DUP_TOP
	  4 STORE_NAME               0 (a)
	  6 LOAD_NAME                0 (a)
	  8 LOAD_CONST               0 (0)
	 10 STORE_SUBSCR
	 12 LOAD_CONST               1 (None)
	 14 RETURN_VALUE
```
::: block <!-- element style="font-size:0.5em" -->
 \*the [`dis` documentation](https://docs.python.org/3/library/dis.html#python-bytecode-instructions) has more info on opcodes.
 
 \*\* `DUP_TOP` was replaced by `COPY` since 3.11
:::

---

# Thank you!

![[Pasted image 20240711115949.png|400]]
[github.com/IljaManakov/lets-investigate-dis](https://github.com/IljaManakov/lets-investigate-dis)

