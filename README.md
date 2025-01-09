# FILE-HANDLING-UTILITY_1

**COMPANY**: CODTECH IT SOLUTIONS

**NAME**:JIDUGU SAI

**INTERN ID**:CT08HFE

**DOMAIN**:JAVA PROGRAMMING

**BATCH DURATION**:DECEMBER 25th,2024 to JANUARY 25th, 2025

**MENTOR NAME**: NEELA SANTHOSH

FILE HANDLING UTILITY

import java.io.*;
import java.nio.file.Files;
import java.nio.file.Paths;
import java.util.List;

public class FileHandlingUtility {

  
    public static void writeFile(String fileName, String content) {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(fileName))) {
            writer.write(content); // Write the content to the file
            System.out.println("Content successfully written to file: " + fileName);
        } catch (IOException e) {
            System.err.println("An error occurred while writing to the file: " + e.getMessage());
        }
    }

    
    public static void readFile(String fileName) {
        try (BufferedReader reader = new BufferedReader(new FileReader(fileName))) {
            String line;
            System.out.println("Reading file: " + fileName);
            while ((line = reader.readLine()) != null) {
                System.out.println(line); 
            }
        } catch (IOException e) {
            System.err.println("An error occurred while reading the file: " + e.getMessage());
        }
    }

    // Method to modify content in a file
    public static void modifyFile(String fileName, String newContent) {
        try {
            List<String> fileContent = Files.readAllLines(Paths.get(fileName));
            fileContent.add(newContent); 

            // Overwrite the file with the updated content
            Files.write(Paths.get(fileName), fileContent);
            System.out.println("File successfully modified: " + fileName);
        } catch (IOException e) {
            System.err.println("An error occurred while modifying the file: " + e.getMessage());
        }
    }

    public static void main(String[] args) {
        String fileName = "sample.txt";

      
        String initialContent = "This is the first line in the file.";
        writeFile(fileName, initialContent);

        
        readFile(fileName);

        
        String newContent = "This is an additional line added to the file.";
        modifyFile(fileName, newContent);

    
        readFile(fileName);
    }
}
