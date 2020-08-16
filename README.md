# File Processing Java

## Reading data using Scanner

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
