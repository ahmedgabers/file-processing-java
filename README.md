# File Processing Java

### Reading data using Scanner

```  File file = new File(pathToFile);

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

### Reading all text from a file as a single string:
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
