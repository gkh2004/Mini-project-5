#include <stdio.h>
#include <ctype.h>

int main() {
    FILE *input = fopen("input.txt", "r");
    FILE *output = fopen("output.txt", "w");
    int ch;

    if (!input || !output) {
        perror("File error");
        return 1;
    }

    while ((ch = fgetc(input)) != EOF) {
        fputc(toupper(ch), output);
    }

    fclose(input);
    fclose(output);
    return 0;
}
#include <fstream>
#include <cctype>

int main() {
    std::ifstream input("input.txt");
    std::ofstream output("output.txt");
    char ch;

    while (input.get(ch)) {
        output.put(std::toupper(ch));
    }

    return 0;
}
import java.io.*;

public class UpperCaseConverter {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new FileReader("input.txt"));
        BufferedWriter writer = new BufferedWriter(new FileWriter("output.txt"));
        int ch;

        while ((ch = reader.read()) != -1) {
            writer.write(Character.toUpperCase(ch));
        }

        reader.close();
        writer.close();
    }
}
input <- file("input.txt", "r")
output <- file("output.txt", "w")
while(length(line <- readLines(input, n = 1, warn = FALSE)) > 0) {
  writeLines(toupper(line), output)
}
close(input)
close(output)


with open("input.txt", "r", encoding="utf-8") as infile,open("output.txt", "w", encoding="utf-8") as outfile:
for line in infile:
        outfile.write(line.upper())
