
# sjc - simplified javac
___

## DISCLAIMER
**DO NOT USE THIS SCRIPT IN ANY OF THE GRADED ASSIGNMENT.**\
**This script is intended to faciliate the project development process by allowing you to compile and execute your Java project faster through an easier syntax.**
___

## Installation
1. Make a ***bin*** directory under your home directory (***~***) if not already there.
    ```shell
    mkdir ~/bin
    ```
2. Download the script to the ***bin*** directory with the following command
    ```shell
    wget -P ~/bin https://raw.githubusercontent.com/JP1128/sjc/master/sjc
    ```
3. Change the permission of the downloaded file to enable execution
    ```shell
    chmod 700 ~/bin/sjc
    ```
4. Add the ***~/bin*** directory to ***PATH*** variable by putting the following line of code at the end of the ***~/.bash_profile***
    ```shell
    export PATH=$PATH:$HOME/bin
    ```
___

## Usage
#### Compile all java source codes in a source directory to an output directory
```shell
sjc sourceDir outputDir
```
- **sourceDir** - directory in which the java source codes are located.
    - If the specified **sourceDir** does not exist, the command will exit with error code **2**.
- **outputDir** - directory to output the compiled classes.
    - If the specified **outputDir** does not exist, a new directory will be created with the same name.
    - If there's an error creating the new directory, the command will exit with error code **3**.

<details>
	<summary>Example</summary> 
	
<p>

	Project // before
	  ┣ src
	  ┃   ┗ apackage
	  ┃     ┣ subpackageA
	  ┃     ┃     ┣ Program1.java
	  ┃     ┃     ┣ Program2.java
	  ┃     ┃     ┗ Program3.java
	  ┃     ┗ subpackageB
	  ┃           ┗ Program4.java
	  ┗ classes
</p>
	
	Project $ sjc src classes

<p>

	Project // after
	  ┣ src
	  ┃   ┗ apackage
	  ┃     ┣ subpackageA
	  ┃     ┃     ┣ Program1.java
	  ┃     ┃     ┣ Program2.java
	  ┃     ┃     ┗ Program3.java
	  ┃     ┗ subpackageB
	  ┃           ┗ Program4.java
	  ┗ classes
	      ┗ apackage
	        ┣ subpackageA
	        ┃     ┣ Program1.class
	        ┃     ┣ Program2.class
	        ┃     ┗ Program3.class
	        ┗ subpackageB
	              ┗ Program4.class
	  
</p>
	
</details>


#### Execute the program
```shell
sjc -e classesDir mainClass
```
- **classesDir** - directory in which the compiled classes are located.
    - If the specified **classesDir** does not exist, the command will exit with error code **6**.
- **mainClass** - name of the driver/main class (class containing the main method).
	- ***Only put the simple name of the class, not the fully-qualified name of the class.***
		- See example
	- Make sure there is no other class under the **classesDir** with the same name.
<details>
	<summary>Example</summary> 
	
<p>

	Project
	  ┣ src
	  ┃   ┗ apackage
	  ┃     ┣ subpackageA
	  ┃     ┃     ┣ Program1.java
	  ┃     ┃     ┣ Program2.java
	  ┃     ┃     ┗ Program3.java
	  ┃     ┗ subpackageB
	  ┃           ┗ Program4.java
	  ┗ classes
	      ┗ apackage
	        ┣ subpackageA
	        ┃     ┣ Program1.class
	        ┃     ┣ Program2.class
	        ┃     ┗ Program3.class
	        ┗ subpackageB
	              ┗ Program4.class
</p>
	
	Project $ sjc -e classes Program1
	# Program1.class or apackage.subpackageA.Program1 will not work
	
</details>


#### Clean the output directory
```shell
sjc -c dir
```
- **dir** - directory to clean.
	- The contents in the specified **dir** will be removed.
	- **dir** will NOT be removed.

## Changelog

