# AWS Challenge Lab: Creating a Hello, World Program

<img width="1227" height="634" alt="Pythonpic 1" src="https://github.com/user-attachments/assets/28a2e077-b1f6-4d80-8e75-9b473590f64b" />


## Hey! Welcome to My AWS Lab Journey 👋

You're looking at the documentation for an AWS Challenge Lab I completed, where I wrote my first Python program using AWS Cloud9. It was a hands-on exercise that pushed me to set up a cloud-based development environment and understand the fundamentals of Python programming.

## What I Set Out to Do

The challenge was straightforward but required real execution:

1. **Access AWS Cloud9 IDE** - Set up a cloud-based development environment
2. **Create a Python file** - Build my workspace and understand file structure
3. **Write my first program** - Follow the time-honored tradition of "Hello, World"
4. **Execute the code** - Run the program and see the output
5. **Understand Python versions** - Learn about Python 2.x vs 3.x compatibility

No shortcuts, no copy-paste solutions—just me, a cloud IDE, and the beginning of my programming journey.

---

## How I Tackled It

### Getting Started: Launching Cloud9

First thing I did was fire up the AWS lab environment and navigated to the Cloud9 service. Cloud9 is a cloud-based IDE that runs entirely in the browser—no local setup required. I opened the `reStart-python-cloud9` environment and watched it spin up. Within seconds, I had a fully functional development environment with Python pre-installed.

**Figure 1: AWS Cloud9 environment loading**
<img width="1212" height="645" alt="PythonPic 6" src="https://github.com/user-attachments/assets/eefd46cc-e4bd-414f-a8db-13a0af378ed4" />



### Setting Up: Creating the Python File
<img width="978" height="581" alt="PythonPic 4" src="https://github.com/user-attachments/assets/7c34315e-0070-4bfa-a1d3-bc79176a1dce" />


I navigated to File > New From Template > Python File, which gave me a pre-formatted Python template. I cleared out the sample code and saved the file as `hello-world.py` in the `/home/ec2-user/environment` directory. The `.py` extension tells the system this is a Python script.

**Figure 3: Creating a new Python file from template**

<img width="1235" height="533" alt="PythonPic 5" src="https://github.com/user-attachments/assets/1957b623-7413-43ee-8559-378d83134979" />


**Figure 4: Saving the file with proper naming**


<img width="862" height="624" alt="PythonPic 7" src="https://github.com/user-attachments/assets/7e5ab018-445e-42b7-81e2-5df5f2e2d830" />


### Understanding the Environment: Terminal Exploration

I opened a new terminal session in Cloud9 (the + icon > New Terminal) and ran some commands to understand my environment:

Here's what I discovered about the Python setup:
- Ran `pwd` to confirm working directory: `/home/ec2-user/environment`
- Checked `python --version` - Found Python 3.6.12 as default
- Checked `python2 --version` - Python 2.7.18 available
- Checked `python3 --version` - Python 3.6.12 (same as default)

This environment was set up with Python 3 as the default, which is modern best practice. Python 2 reached end-of-life in 2020, so using Python 3.x is the right choice.

**Figure 5: Terminal commands checking Python versions**

<img width="769" height="519" alt="PythonPic 8" src="https://github.com/user-attachments/assets/af093665-2f37-4aec-a3b4-80d8f899cbbc" />


### The Main Event: Writing the Program

Now came the actual coding. I typed the classic first program every programmer writes:

```python
print("Hello, World")
```

That's it. One line. But this single line represents something important—it's the traditional first step in learning any programming language. The `print()` function outputs text to the console. Simple, but fundamental.

**Figure 6: The complete Hello World program**

<img width="969" height="636" alt="PythonPic 9" src="https://github.com/user-attachments/assets/8e065538-c4e9-45ed-a304-0e30a95dc82e" />

### The Moment of Truth: Running the Program

I saved the file (File > Save) and clicked the green Run button at the top of the IDE. The bottom pane of Cloud9 became active, showing the terminal output. And there it was:

```
Hello, World
```

The program executed successfully. My first Python program worked on the first try.

**Figure 7: Program execution and output**

<img width="1275" height="594" alt="Pythonpic10" src="https://github.com/user-attachments/assets/3bd7ee4c-a507-40a2-95d0-62d5636dc406" />

---

## What I Learned

This wasn't just about printing text to a screen. The real value was in:

- **Cloud-Based Development** - I experienced how cloud IDEs eliminate local setup complexity and provide consistent environments
- **Python Fundamentals** - I learned about Python versions, backward compatibility, and why Python 3.x is the modern standard
- **Development Workflow** - I practiced the basic cycle: write code, save, execute, observe output
- **File Management** - I understood file extensions, directory structures, and workspace organization

It's one thing to read about programming. It's another to set up an environment, write actual code, and see it execute successfully.

---

## 
---

## The Code

```python
print("Hello, World")
```

**Explanation:**
- `print()` - Built-in Python function that outputs text to the console
- `"Hello, World"` - String literal enclosed in double quotes
- The function takes the string as an argument and displays it

---

## Python Version Comparison

### Python 2.x vs Python 3.x

| Aspect | Python 2.x | Python 3.x |
|--------|-----------|-----------|
| **Status** | End-of-life (2020) | Actively maintained |
| **Print Statement** | `print "Hello"` | `print("Hello")` |
| **Default String Type** | ASCII | Unicode |
| **Division** | `5/2 = 2` (integer) | `5/2 = 2.5` (float) |
| **Best Practice** | Legacy only | Use for all new projects |

### Version Check Commands

```bash
# Check default Python version
python --version

# Check Python 2 version (if installed)
python2 --version

# Check Python 3 version
python3 --version
```

---

## Want to Try This Yourself?

If you have access to AWS and want to replicate this:

1. Launch AWS Cloud9 from the AWS Management Console
2. Create a new Python file from the template
3. Delete the sample code and write your own `print()` statement
4. Save the file with a `.py` extension
5. Click the Run button to execute your program
6. Observe the output in the terminal pane

It's the simplest possible exercise, but it builds confidence and establishes the foundation for everything that follows.

---

## Tech Stack

- **Cloud Platform:** AWS Cloud9 (Cloud-based IDE)
- **Programming Language:** Python 3.6.12
- **Development Environment:** Browser-based with integrated terminal
- **Operating System:** Amazon Linux (underlying EC2 instance)

---

## Key Concepts

### Why "Hello, World"?

The "Hello, World" program is a programming tradition dating back to the 1970s. It serves several purposes:

1. **Verifies installation** - Confirms the programming environment is set up correctly
2. **Demonstrates syntax** - Shows the basic structure of the language
3. **Builds confidence** - Provides immediate success for beginners
4. **Establishes workflow** - Introduces the edit-save-run cycle

### The `print()` Function

The `print()` function is one of Python's most fundamental built-in functions:

- **Purpose:** Outputs data to the console/terminal
- **Syntax:** `print(object, ...)`
- **Common uses:** Debugging, displaying results, user communication
- **Note:** In Python 2, `print` was a statement; in Python 3, it's a function requiring parentheses

---

## Cloud9 Advantages

Using AWS Cloud9 for development provides several benefits:

- **No local setup** - Everything runs in the cloud
- **Consistent environment** - Same setup for all students/developers
- **Collaborative features** - Share environments with team members
- **Pre-configured tools** - Python, terminal, and dependencies already installed
- **Accessible anywhere** - Just need a browser and internet connection

---

## Next Steps

After completing "Hello, World," typical next steps in Python learning include:

1. Variables and data types
2. User input with `input()`
3. Conditional statements (if/else)
4. Loops (for/while)
5. Functions and modules

But every programming journey starts with that first `print()` statement.

---

*Completed as part of AWS Training & Certification Challenge Lab*
