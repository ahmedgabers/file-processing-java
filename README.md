# Reading Files

#### Reading data using Scanner

```  
File file = new File(pathToFile);

try (Scanner scanner = new Scanner(file)) {
    while (scanner.hasNext()) {
        System.out.print(scanner.nextLine() + " ");
    }
} catch (FileNotFoundException e) {
    System.out.println("No file found: " + pathToFile);
}
```
```
try (Scanner scanner = new Scanner(Paths.get("file.txt"))) {}
```

#### Reading all text from a file as a single string:
```
public class ReadingFileDemo {
    public static String readFileAsString(String fileName) throws IOException {
        return new String(Files.readAllBytes(Paths.get(fileName)));
    }

    public static void main(String[] args) {
        String pathToHelloWorldJava = "/home/username/Projects/hello-world/HelloWorld.java";
        try {
            System.out.println(readFileAsString(pathToHelloWorldJava));
        } catch (IOException e) {
            System.out.println("Cannot read file: " + e.getMessage());
        }
    }
}
```

#### Managing Files:

###### Create file:

```
File file = new File("/home/username/Documents/file.txt");
try {
    boolean createdNew = file.createNewFile();
    if (createdNew) {
        System.out.println("The file was successfully created.");
    } else {
        System.out.println("The file already exists.");
    }
} catch (IOException e) {
    System.out.println("Cannot create the file: " + file.getPath());
}
```

###### Create directory:

```
File file = new File("/home/art/Documents/dir");

boolean createdNewDirectory = file.mkdir();
if (createdNewDirectory) {
    System.out.println("It was successfully created.");
} else {
    System.out.println("It was not created.");
}
```

###### Create directories:

```
File file = new File("/home/art/Documents/dir/dir/dir");

boolean createdNewDirectory = file.mkdirs();
if (createdNewDirectory) {
    System.out.println("It was successfully created.");
} else {
    System.out.println("It was not created.");
}
```

###### Remove files and directories:

```
File file = new File("/home/art/Documents/dir/dir/dir");
        
if (file.delete()) {
    System.out.println("It was successfully removed.");
} else {
    System.out.println("It was not removed.");
}
```


```
public void deleteDirRecursively(File dir) {
    File[] children = dir.listFiles();
    for (File child : children) {
        if (child.isDirectory()) {
            deleteDirRecursively(child);
        } else {
            child.delete();
        }
    }

    dir.delete();
}
```


###### Renaming and moving files and directories

```
File file = new File("/home/art/Documents/dir/filename.txt");

boolean renamed = file.renameTo(new File("/home/art/Documents/dir/newname.txt"));


File file = new File("/home/art/Documents/dir/filename.txt");
File renamedFile = new File("/home/art/Documents/dir/newname.txt");

boolean renamed = file.renameTo(renamedFile);
if (renamed) {
    System.out.println("It was successfully renamed.");
} else {
    System.out.println("It was not renamed.");
}
```
<p align=center>======================</p>
# Writing Files

#### The FileWriter class
```
FileWriter(String fileName);
FileWriter(String fileName, boolean append);
FileWriter(File file);
FileWriter(File file, boolean append);
```
```
File file = new File("/home/username/path/to/your/file.txt");

try (FileWriter writer = new FileWriter(file)) {
    writer.write("Hello, World");
} catch (IOException e) {
    System.out.printf("An exception occurs %s", e.getMessage());
}
```

#### The PrintWriter class
```
File file = new File("/home/art/Documents/file.txt");
try (PrintWriter printWriter = new PrintWriter(file)) {
    printWriter.print("Hello"); // prints a string
    printWriter.println("Java"); // prints a string and then terminates the line
    printWriter.println(123); // prints a number
    printWriter.printf("You have %d %s", 400, "gold coins"); // prints a formatted string
} catch (IOException e) {
    System.out.printf("An exception occurs %s", e.getMessage());
}
```
