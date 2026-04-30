# 🐚 Experiment 3 — Bash Shell Scripting

> **Course:** Introduction to Linux with Bash Scripting Lab  
> **CO Mapped:** CO2 — Ability to write Bash scripts for automation and task execution | CO4 — Use of conditional statements and loops for control flow

---

## 🎯 Learning Outcomes

After completing this experiment, you will be able to:

- **LO1:** Create interactive shell scripts using user input
- **LO2:** Use positional parameters in Bash scripts
- **LO3:** Perform arithmetic operations in shell scripts
- **LO4:** Implement conditional statements and loops for decision-making and repetition

---

## 📖 Theory

### Shell Programming
Shell scripting automates tasks by writing a sequence of Linux commands in a script file executed by the shell.

### Key Concepts

| Concept | Description |
|---|---|
| `read` | Accepts input from the user during execution |
| `$0, $1, $2...` | Positional parameters — script name and arguments |
| `$(( ))` | Arithmetic evaluation |
| `if / elif / else` | Conditional decision-making |
| `for / while` | Loop constructs for repetition |

---

## 🗂️ Commands Reference

| Command | Description |
|---|---|
| `read` | Accept user input |
| `echo` | Display output |
| `$(( ))` | Arithmetic operations |
| `if, elif, else` | Conditional statements |
| `for, while` | Loop constructs |
| `chmod +x` | Make script executable |

---

## 🚀 Procedure & Output

### A. Interactive Shell Script — `interactive.sh`

```bash
nano interactive.sh
```

**Script:**
```bash
#!/bin/bash
echo "Enter your name:"
read name
echo "Welcome $name"
```

```bash
chmod +x interactive.sh
./interactive.sh
```

**Output:**
```
Enter your name:
Sankarshan
Welcome Sankarshan
```

---

### B. Positional Parameters — `params.sh`

```bash
nano params.sh
```

**Script:**
```bash
#!/bin/bash
echo "Script Name: $0"
echo "First Argument: $1"
echo "Second Argument: $2"
```

```bash
chmod +x params.sh
./params.sh Linux Bash
```

**Output:**
```
Script Name: ./params.sh
First Argument: Linux
Second Argument: Bash
```

---

### C. Arithmetic Operations — `arithmetic.sh`

```bash
nano arithmetic.sh
```

**Script:**
```bash
#!/bin/bash
a=10
b=5
sum=$((a + b))
echo "Sum = $sum"
```

```bash
chmod +x arithmetic.sh
./arithmetic.sh
```

**Output:**
```
Sum=15
```

---

### D. Conditional Statement — `condition.sh`

```bash
nano condition.sh
```

**Script:**
```bash
#!/bin/bash
echo "Enter a number:"
read num
if [ $num -gt 0 ]
then
    echo "Positive number"
else
    echo "Zero or Negative number"
fi
```

```bash
chmod +x condition.sh
./condition.sh
```

**Output:**
```
Enter a number:
2
Positive number
```

---

### E. Loop Constructs — `loop.sh`

```bash
nano loop.sh
```

**Script:**
```bash
#!/bin/bash
for i in 1 2 3 4 5
do
    echo "Iteration $i"
done
```

```bash
chmod +x loop.sh
./loop.sh
```

**Output:**
```
Iteration 1
Iteration 2
Iteration 3
Iteration 4
Iteration 5
```

---

## ✅ Expected Output

- Interactive script accepts name and prints welcome message
- Positional parameters script correctly reads command-line arguments
- Arithmetic script calculates and displays the sum
- Conditional script identifies positive / zero / negative numbers
- Loop script prints iterations 1 through 5

---

## 📸 Submission Requirements

Attach screenshots of:
- [ ] Execution of `interactive.sh` with your name as input
- [ ] Execution of `params.sh` with two arguments
- [ ] Output of `arithmetic.sh`
- [ ] Execution of `condition.sh` with a number input
- [ ] Output of `loop.sh` showing all iterations

---

## 📝 Result

Bash shell scripts for interactive input, positional parameters, arithmetic operations, conditional statements, and loop constructs were successfully written and executed. The student demonstrated the ability to automate basic computational and logical tasks using shell scripting.
