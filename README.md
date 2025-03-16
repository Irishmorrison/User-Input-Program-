# User-Input-Program-
Here is the source code:

#include <iostream>
#include <fstream>
#include <string>
#include <algorithm>

void reverseContent(const std::string& inputFile, const std::string& outputFile) {
    std::ifstream inFile(inputFile);
    std::string content;
    
    if (inFile) {
        // Read the entire content of the input file
        std::getline(inFile, content, '\0'); // Read until EOF
        inFile.close();
    } else {
        std::cerr << "Error opening file: " << inputFile << std::endl;
        return;
    }

    // Reverse the content
    std::reverse(content.begin(), content.end());

    // Write the reversed content to the output file
    std::ofstream outFile(outputFile);
    if (outFile) {
        outFile << content;
        outFile.close();
    } else {
        std::cerr << "Error opening file: " << outputFile << std::endl;
    }
}

int main() {
    std::string inputFileName = "CSC450_CT5_mod5.txt";
    std::string outputFileName = "CSC450-mod5-reverse.txt";
    std::string userInput;

    // Obtain input from the user
    std::cout << "Enter text to append to " << inputFileName << ": ";
    std::getline(std::cin, userInput);

    // Append user input to the specified file
    std::ofstream outFile(inputFileName, std::ios::app);
    if (outFile) {
        outFile << userInput << std::endl;
        outFile.close();
    } else {
        std::cerr << "Error opening file: " << inputFileName << std::endl;
    }

    // Call function to reverse the content
    reverseContent(inputFileName, outputFileName);

    std::cout << "Data appended and reversed content written to " << outputFileName << std::endl;
    return 0;
}


