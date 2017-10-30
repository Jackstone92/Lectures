# Reading/writing data from/to a file

---

# The concept of a **stream**
- Use of files
  - Store Java classes, programs
  - Store pictures, music videos
  - Can also use files to store program I/O
- A **stream** is a flow of input or output data
  - Characters
  - Numbers
  - Bytes

Streams are implemented as objects of special **stream** classes

# Writing/reading to/from a text file
## Creating a text file
- Package *java.io* contains a number of classes to deal with files
  - eg. **PrintWriter** class
    - Defines methods needed to create and write to a text file

To open the file:
- Declare a *stream variable* for referencing the stream
- Invoke **PrintWriter** constructor, pass file name as argument

Initially, the file is empty
- Once created, it may be written to using method **println**
- Data goes initially to a *"buffer" in memory*
  - When the buffer is full, data goes to the file
- *Closing a file* empties the *buffer*, disconnects from the stream

### **PrintWriter**
- Composed from several objects
```java
PrintWriter out = new PrintWriter(new FileWriter(dstFileName, false), true);
```
- Requires **throws FileNotFoundException**, which is a sub-class of **IOException**

Methods:
- **print(), println()**: *buffers* data to write
- **flush()**: sends buffered output to destination
- **close()**: flushes and closes stream

```java
import java.io.*;

class PrintTextFile {
  public static void main(String[] args) {
    File file = new File("output.txt"); // creates a File object that represents the disk file //
    PrintWriter print = new PrintWriter(file); // connects the file to an output PrintStream //

    print.println("Our only real hope for democracy is");
    print.println("that we get the money out of politics entirely");
    print.println("and establish a system of publicly funded elections.");
    print.println("Noam Chomsky.");

    print.close();
  }
}
```
Results in:
> Our only real hope for democracy is
that we get the money out of politics entirely
and establish a system of publicly funded elections.
Noam Chomsky.

### PrintStream
- Used for **character output to a text file**
- The program first creates a File object that represents the disk file
```java
File file = new File("output.txt");
```
- The following line connects the file to an output PrintStream
```java
PrintStream print = new PrintStream(file);
```

### output.txt
- If the file already exists its contents will be destroyed unless the user does not have permission to alter the file. If this is the case, an IOException will be thrown and the program will end. (Most modern operating systems implement **file permissions**, where files can be marked read only.)
- Several lines of characters are sent to the output stream which is now connected to the file. Each line ends with the control characters that separate lines:
```java
print.println("Our only real hope for democracy is");
print.println("that we get the money out of politics entirely");
print.println("and establish a system of publicly funded elections.");
print.println("Noam Chomsky.");
```
- Finally, the stream is **closed**. This means the disk file is completed and now is available for other programs to use
```java
print.close();
```

# Overwriting a file -- !!!
- A file has two names in the program
  - File name used by the operating system
  - The stream name variable
- Opening, writing to file **overwrites** pre-existing file in directory!
```java
import java.io.*;

Class FileOverWriting
{
  public static void main ( String[] args ) throws IOException
  {
    File file = new File("output.txt");  //creates a File object that represents the disk file.
    PrintWriter print = new PrintWriter(file); //connects the file to an output PrintStream.

    print.println("Our only real hope for democracy is");
    print.println("that we get the money out of politics entirely");
    print.println("and establish a system of publicly funded elections.");
    print.println("Noam Chomsky.");

    PrintWriter print1 = new PrintWriter(file); //connects the file to an output PrintStream.
    print1.println("What should i do to get a first class degree?");
    print1.println("It is simple, work harder!");
    print.close();
    print1.close();
  }
}
```
Results in:
> What should i do to get a first class degree? It is simple, work harder!

# Appending to a text file
- Opening a file begins with an empty file
  - If already exists, will be overwritten
- Some situations require appending data to existing file

Appending data can be achieved by the following declaration:
```java
outputStream = new PrintWriter(new FileOutputStream(fileName, true));
```
- Method `println` would append data at end

```java
import java.io.*;

Class AppendFile {
  public static void main ( String[] args ) throws IOException {
    File file = new File("output.txt");  //creates a File object that represents the disk file.
    PrintWriter print = new PrintWriter(new FileOutputStream(file, true));

    print.println("Our only real hope for democracy is");
    print.println("that we get the money out of politics entirely");
    print.println("and establish a system of publicly funded elections.");
    print.println("Noam Chomsky.");

    print.close();
  }
}
```
If output text already contained "What should I do to get a first class degree? It is simple, work harder!":
Results in:
> What should I do to get a first class degree?
It is simple, work harder!
Our only real hope for democracy is
that we get the money out of politics entirely
and establish a system of publicly funded elections.
Noam Chomsky.

# Reading files
- The same applies for both console input and file input
- We can use a different version of a **Scanner** that takes a **File** instead of **System.in**

To read from a disk file, construct a **FileReader**
- Then use **FileReader** to construct a **Scanner** object
```java
FileReader reader = new FileReader("input.txt");
Scanner fin = new Scanner(reader);
```

- You can use **File** instead of **FileReader**
  - Has an `exists()` method we can call to avoid **FileNotFoundException**
```java
File file = new File("input.txt");
Scanner fin;

if(file.exists()) {
  fin = new Scanner(file);
} else {
  // ask for another file //
}
```

Once we have a Scanner, we can use methods:
- `next`, `nextLine`, `nextInt` etc.

## File class
- **java.io.File**
Constructors:
- `File(<full path>)`
- `File(<path>, <filename>)`

Methods:
- `exists()`
- `canRead()`, `canWrite()`
- `isFile()`, `isDirectory()`

## FileReader class
- **java.io.FileReader**
- Associated with **File** object
- Translates data bytes from File object into a stream of characters (much like InputStream vs InputStreamReader)

Constructors:
- `FileReader(<File object>)`

Methods:
- `read()`, `readLine()`
- `close()`

# Examples
## Read a file line-by-line using BufferedReader
```java
import java.io.*;

class FileReaderLine {
  public static void main ( String[] args ) throws IOException {
    File fileName = new File("output.txt"); // make a file object
    FileReader fr = new FileReader(fileName);  //Get data from this file using a file reader.
    BufferedReader br = new BufferedReader(fr);  //To store the contents read via File Reader

    //Read br and store a line in 'data', print data
    String str =null;
    while((str= br.readLine()) !=null) { // check for end of file
      System.out.println(str);  
    }
    fr.close();
  }
}
```

## Read a file character-by-character using BufferedReader
```java
import java.io.*;

class FileReaderChar {
  public static void main ( String[] args ) throws IOException {
    File fileName = new File("output.txt"); // make a file object
    FileReader fr = new FileReader(fileName);  //Get data from this file using a file reader.
    BufferedReader br = new BufferedReader(fr);  //To store the contents read via File Reader
    int n;

    //Read br and store a line in 'data', print data
    while((n=br.read()) != -1) {  // check for end of file
       System.out.print((char)n);  //print char
    }
    fr.close();
  }
}
```

### We can also use Scanner to read a File word-by-word

| Scanner_object_name.hasNext() | Returns true if more input data is available to be read by the method next |
| --- | --- |
| Scanner_Object_Name.hasNextDouble() | Returns true if more input data is available to be read by the method nextDouble |
| Scanner_Object_Name.hasNextInt() | Returns true if more input data is available to be read by the method nextInt |
| Scanner_Object_Name.hasNextLine() | Returns true if more input data is available to be read by the method nextLine |

## Read a file line-by-line using Scanner
```java
import java.io.*;
import java.util.Scanner;

class ReadFromFileLine {
  public static void main ( String[] args ) throws IOException {
    // Prompt for and open the input file
    Scanner user = new Scanner(System.in);
    System.out.print("File name?");
    String fileName = user.next().trim();  
    Scanner scan = new Scanner( new File(fileName) );

    while(scan.hasNextLine()) { // check for end of file
      System.out.println(scan.nextLine());  //print next line
    }
  }
}
```

## Read a file word-by-word using Scanner
```java
import java.io.*;
import java.util.Scanner;

class ReadFromFileWord {
  public static void main ( String[] args ) throws IOException {
    // Prompt for and open the input file
    Scanner user = new Scanner(System.in);
    System.out.print("File name? ");
    String fileName = user.next().trim();  
    Scanner scan = new Scanner( new File(fileName) );

    while(scan.hasNext()) { // check for end of file
      System.out.println(scan.Next());  //print next Line
    }
  }
}
```

## Add numbers from file
```java
import java.io.*;
import java.util.Scanner;

class AddAllFromFile {
  public static void main ( String[] args ) throws IOException {
    int sum = 0; // initialise sum

    Scanner user = new Scanner(System.in);  // Prompt and open input file
    System.out.print("File name? ");
    String fileName = user.next().trim();
    Scanner scan = new Scanner( new File(fileName) );

    while (scan.hasNextInt()) {
      sum = sum + scan.nextInt();   // add to the sum
    }
    System.out.println( "The sum is: " + sum );
  }
}
```

## Average of number from file
```java
import java.io.*;
import java.util.Scanner;

class AverageOfAll {
  public static void main ( String[] args ) throws IOException {
    int sum = 0, count=0;  // initialise sum and count
    double average =0;
    Scanner user = new Scanner(System.in);  // Prompt and open input file
    System.out.print("File name? ");
    String fileName = user.next().trim();
    Scanner scan = new Scanner(new File(fileName));

    while (scan.hasNextInt()) {
      sum = sum + scan.nextInt();   // add to the sum
      count++;   // increment count  
    }

    if(count >0) average = sum/count*1.0;
    System.out.println( "The average is: " + average);
  }
}
```

## Input/Output files from user input
```java
import java.util.Scanner;
import java.io.*;

class NamedFileInOut {
  public static void main (String[] args) throws IOException {
    // Scanner for user input
    Scanner user = new Scanner(System.in);
    String  inputFileName, outputFileName;

    // prepare the input file
    System.out.print("Input File Name: ");  // user interaction
    inputfileName = user.nextLine().trim();  // trim any white space from the file.
    File input = new File(inputfileName );      
    Scanner scan = new Scanner(input );      

    // prepare the output file
    System.out.print("Output File Name: ");  // user interaction
    outputfileName = user.nextLine().trim();  // remove white space
    File output = new File( outputfileName );
    PrintStream  print = new PrintStream(output);    // use file output name declaration  file to print into  output
  }
}
```

## Reading a file character-by-character using FileInputStream
```java
import java.io.*;

class ReadFromFileChar {
  public static void main ( String[] args ) throws IOException {
    FileInputStream fileInput = new FileInputStream("file.txt");
    int r;

    while ((r = fileInput.read()) != -1) {  // check for end of file
      char c = (char) r;
      System.out.print(c);
    }

    fileInput.close();
  }
}
```

## Copy a file character-by-character
```java
import java.io.*;
import java.util.Scanner;

class CopyFileCharbyChar {
  public static void main ( String[] args ) throws IOException {
    FileInputStream fileInput = new FileInputStream("file.txt");
    FileOutputStream fileOutput = new FileOutputStream(“out.txt”)
    int r;

    while ((r = fileInput.read()) != -1) {  // check for end of file
      fileOutput.write(r);        
    }

    fileInput.close();
    fileOutput.close();
  }
}
```

## Counts number of characters in a file using Scanner
```java
import java.io.*;
import java.util.Scanner;

class FileLineCount {
  public static void main ( String[] args ) throws IOException {
    // Prompt for and open the input file
    Scanner user = new Scanner(System.in);
    System.out.print("File name?");
    String fileName = user.next().trim();
    Scanner scan = new Scanner( new File(fileName) );
    int counter=0;

    while(scan.hasNextLine()) {
      counter++;  
      scan.nextLin();
    }

    System.out.println(fileName + "contains" + counter + "Lines");
    fileInput.close();
  }
}
```

## Counts number of characters in a file using BufferedReader
```java
import java.io.*;
import java.util.Scanner;

class FileLineCount {
  public static void main ( String[] args ) throws IOException {
    // Prompt for and open the input file
    Scanner scan = new Scanner(System.in);
    System.out.println("Enter the file name:");
    String fileName = scan.next().trim();
    FileInputStream fileInput = new FileInputStream(fileName);
    BufferedReader br= new BufferedReader(fileInput);
    int counter=0;

    while ((br.readLine()) !=  null) {  // check for end of file
      counter++;   
    }

    System.out.println(fileName + "contains" + counter + "Lines");
    fileInput.close();
  }
}
```
