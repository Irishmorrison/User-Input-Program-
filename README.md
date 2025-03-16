# User-Input-Program-
Here is the source code:

#include <iostream>
#include <fstream>
#include <string>
#include <algorithm>

using namespace std;

// Function to reverse a string
string reverseString(const string &str) {
    string reversedStr = str;
    reverse(reversedStr.begin(), reversedStr.end());
    return reversedStr;
}

int main() {
    string inputString;
    string filePath = "CSC450_CT5_mod5.txt";
    string reverseFilePath = "CSC450-mod5-reverse.txt";

    // Step 1: Get user input
    cout << "Enter a string to store in the file: ";
    getline(cin, inputString);  // Use getline to allow spaces in input

    // Step 2: Append user input to the file
    ofstream outFile(filePath, ios::app);
    if (outFile.is_open()) {
        outFile << inputString << endl;  // Append the input
        outFile.close();
    } else {
        cerr << "Unable to open file for writing." << endl;
        return 1; // Exit with error
    }

    // Step 3: Reverse the contents of the file
    string content;
    ifstream inFile(filePath);
    if (inFile.is_open()) {
        string line;
        while (getline(inFile, line)) {
            content += line + '\n';  // Read the entire file
        }
        inFile.close();
    } else {
        cerr << "Unable to open file for reading." << endl;
        return 1; // Exit with error
    }

    // Step 4: Write reversed content to a new file
    ofstream revFile(reverseFilePath);
    if (revFile.is_open()) {
        revFile << reverseString(content);  // Write the reversed content
        revFile.close();
    } else {
        cerr << "Unable to open reverse file for writing." << endl;
        return 1; // Exit with error
    }

    cout << "Data has been written and reversed." << endl;
    return 0;
}
