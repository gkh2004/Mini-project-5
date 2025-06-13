# Mini-project-5
#include <stdio.h>
#include <ctype.h>
#include <time.h>

int main() {
    FILE *in = fopen("input.txt", "r");
    FILE *out = fopen("output.txt", "w");
    char buffer[1024 * 1024]; // 1MB buffer
    size_t bytes;
    clock_t start = clock();

    while ((bytes = fread(buffer, 1, sizeof(buffer), in)) > 0) {
        for (size_t i = 0; i < bytes; i++) {
            buffer[i] = toupper(buffer[i]);
        }
        fwrite(buffer, 1, bytes, out);
    }

    clock_t end = clock();
    printf("Time: %.2f seconds\n", (double)(end - start) / CLOCKS_PER_SEC);
    fclose(in); fclose(out);
    return 0;
}
#include <iostream>
#include <fstream>
#include <cctype>
#include <ctime>

int main() {
    std::ifstream in("input.txt", std::ios::binary);
    std::ofstream out("output.txt", std::ios::binary);
    const size_t bufferSize = 1024 * 1024;
    char* buffer = new char[bufferSize];
    std::clock_t start = std::clock();

    while (in.read(buffer, bufferSize) || in.gcount()) {
        size_t bytes = in.gcount();
        for (size_t i = 0; i < bytes; ++i) buffer[i] = toupper(buffer[i]);
        out.write(buffer, bytes);
    }

    std::clock_t end = std::clock();
    std::cout << "Time: " << (end - start) / (double) CLOCKS_PER_SEC << " seconds\n";
    delete[] buffer;
}
import java.io.*;

public class UpperCaseConverter {
    public static void main(String[] args) throws IOException {
        long start = System.currentTimeMillis();
        BufferedReader reader = new BufferedReader(new FileReader("input.txt"));
        BufferedWriter writer = new BufferedWriter(new FileWriter("output.txt"));
        String line;
        while ((line = reader.readLine()) != null) {
            writer.write(line.toUpperCase());
            writer.newLine();
        }
        reader.close();
        writer.close();
        long end = System.currentTimeMillis();
        System.out.println("Time: " + (end - start) / 1000.0 + " seconds");
    }
}
start <- Sys.time()
con_in <- file("input.txt", "r")
con_out <- file("output.txt", "w")
repeat {
  lines <- readLines(con_in, n = 10000)
  if (length(lines) == 0) break
  writeLines(toupper(lines), con_out)
}
close(con_in)
close(con_out)
end <- Sys.time()
print(paste("Time:", round(difftime(end, start, units = "secs"), 2)))
import time

start = time.time()
with open("input.txt", "r") as fin, open("output.txt", "w") as fout:
    while True:
        data = fin.read(1024 * 1024)
        if not data:
            break
        fout.write(data.upper())
end = time.time()
print(f"Time: {end - start:.2f} seconds")
