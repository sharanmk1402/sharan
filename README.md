C Program 1111111111111111111111 -----------------------------------------------------------------------------------------------------------------------------

#include <stdio.h> 
 
int main() { 
    double num1, num2; 
    char operator; 
 
    // Display the menu 
    printf("Simple Calculator\n"); 
    printf("====================\n"); 
    printf("Choose an operator (+, -, *, /): "); 
    scanf(" %c", &operator);  // Notice the space before %c to consume any leftover newline character 
 
    // Ask user to input two numbers 
    printf("Enter the first number: "); 
    scanf("%lf", &num1); 
    printf("Enter the second number: "); 
    scanf("%lf", &num2); 
 
    // Perform the operation based on the chosen operator 
    switch (operator) { 
        case '+': 
            printf("%.2lf + %.2lf = %.2lf\n", num1, num2, num1 + num2); 
            break; 
        case '-': 
            printf("%.2lf - %.2lf = %.2lf\n", num1, num2, num1 - num2); 
            break; 
        case '*': 
            printf("%.2lf * %.2lf = %.2lf\n", num1, num2, num1 * num2); 
            break; 
        case '/': 
            // Handle division by zero 
            if (num2 != 0) { 
                printf("%.2lf / %.2lf = %.2lf\n", num1, num2, num1 / num2); 
            } else { 
                printf("Error! Division by zero.\n"); 
            } 
            break; 
        default: 
            printf("Invalid operator! Please use one of the following: +, -, *, /\n"); 
            break; 
    } 
 
    return 0; 
} 
 
 
C Program 22222222222 ------------------------------------------------------------------------------------------------------------------------------------------

#include <stdio.h> 
 
// Function to perform binary search 
int binarySearch(int arr[], int size, int target) { 
    int left = 0, right = size - 1; 
 
    while (left <= right) { 
        int mid = left + (right - left) / 2; // Calculate middle index 
 
        // Check if target is present at mid 
        if (arr[mid] == target) { 
            return mid;  // Target found, return the index 
        } 
 
        // If target is greater, ignore the left half 
        if (arr[mid] < target) { 
            left = mid + 1; 
        } 
        // If target is smaller, ignore the right half 
        else { 
            right = mid - 1; 
        } 
    } 
 
    return -1;  // Target not found 
} 
 
int main() { 
    int arr[] = {2, 5, 8, 12, 16, 23, 42, 56, 67, 89};  // Sorted array 
    int size = sizeof(arr) / sizeof(arr[0]);  // Size of the array 
    int target; 
 
    // Ask user for the target element to search for 
    printf("Enter the number to search: "); 
    scanf("%d", &target); 
 
    // Perform binary search and get the result 
    int result = binarySearch(arr, size, target); 
 
    // Output result 
    if (result != -1) { 
        printf("Element %d found at index %d.\n", target, result); 
    } else { 
        printf("Element %d not found in the array.\n", target); 
    } 
 
    return 0; 
} 
 
C Program 3333333333333333333333333333------------------------------------------------------------------------------------------------------------------------------------------ 
 
#include <stdio.h> 
 
// Function to perform Bubble Sort 
void bubbleSort(int arr[], int size) { 
    int i, j, temp; 
 
    // Outer loop for the number of passes 
    for (i = 0; i < size - 1; i++) { 
        // Inner loop for comparing adjacent elements 
        for (j = 0; j < size - 1 - i; j++) { 
            // If the current element is greater than the next, swap them 
            if (arr[j] > arr[j + 1]) { 
                // Swap the elements 
                temp = arr[j]; 
                arr[j] = arr[j + 1]; 
                arr[j + 1] = temp; 
            } 
        } 
    } 
} 
 
// Function to print the array 
void printArray(int arr[], int size) { 
    for (int i = 0; i < size; i++) { 
        printf("%d ", arr[i]); 
    } 
    printf("\n"); 
} 
 
int main() { 
    int N, i; 
 
    // Get the number of elements to sort 
    printf("Enter the number of elements: "); 
    scanf("%d", &N); 
 
int arr[N]; 
// Input the elements 
printf("Enter the elements: \n"); 
for (i = 0; i < N; i++) { 
scanf("%d", &arr[i]); 
} 
// Display the array before sorting 
printf("\nArray before sorting:\n"); 
printArray(arr, N); 
// Call bubbleSort to sort the array 
bubbleSort(arr, N); 
// Display the array after sorting 
printf("\nArray after sorting:\n"); 
printArray(arr, N); 
return 0; 
} 




Program 444444444444444444444-----------------------------------------------------------------------------------------------------------

Implement Matrix multiplication and validate the rules of multiplication. 
2*2 Matrix , 3* 3 Matrix 
#include <stdio.h> 
 
// Function to validate matrix multiplication rules 
int validateMultiplication(int rows1, int cols1, int rows2, int cols2) { 
    if (cols1 != rows2) { 
        printf("Matrix multiplication not possible. Number of columns in Matrix 1 (%d) must be 
equal to the number of rows in Matrix 2 (%d).\n", cols1, rows2); 
        return 0; 
    } 
    return 1; 
} 
 
// Function to perform matrix multiplication 
void multiplyMatrices(int mat1[10][10], int mat2[10][10], int result[10][10], int rows1, int cols1, 
int rows2, int cols2) { 
    int i,j,k; 
 for (i = 0; i < rows1; i++) { 
        for (j = 0; j < cols2; j++) { 
            result[i][j] = 0; // Initialize the result matrix element to 0 
            for (k = 0; k < cols1; k++) { 
                result[i][j] += mat1[i][k] * mat2[k][j]; 
            } 
        } 
    } 
} 
 
// Function to display a matrix 
void displayMatrix(int matrix[10][10], int rows, int cols)  
{ 
 int i,j; 
    for ( i = 0; i < rows; i++) { 
        for ( j = 0; j < cols; j++) { 
            printf("%d ", matrix[i][j]); 
        } 
        printf("\n"); 
    } 
} 
 
int main() { 
    int mat1[10][10], mat2[10][10], result[10][10]; 
    int rows1, cols1, rows2, cols2,i,j; 
 
    // Input dimensions of the first matrix 
    printf("Enter the number of rows and columns for Matrix 1: "); 
    scanf("%d %d", &rows1, &cols1); 
 
    // Input dimensions of the second matrix 
    printf("Enter the number of rows and columns for Matrix 2: "); 
    scanf("%d %d", &rows2, &cols2); 
 
    // Validate multiplication rule 
    if (!validateMultiplication(rows1, cols1, rows2, cols2)) { 
        return 0; // Exit if multiplication is not possible 
    } 
 
    // Input elements of the first matrix 
    printf("Enter elements of Matrix 1 (%d x %d):\n", rows1, cols1); 
    for (i = 0; i < rows1; i++)  
 { 
        for ( j = 0; j < cols1; j++) { 
            scanf("%d", &mat1[i][j]); 
        } 
    } 
 
    // Input elements of the second matrix 
    printf("Enter elements of Matrix 2 (%d x %d):\n", rows2, cols2); 
    for (i = 0; i < rows2; i++) { 
        for (j = 0; j < cols2; j++) { 
            scanf("%d", &mat2[i][j]); 
        } 
    } 
// Perform matrix multiplication 
multiplyMatrices(mat1, mat2, result, rows1, cols1, rows2, cols2); 
// Display the result 
printf("Resultant Matrix (%d x %d):\n", rows1, cols2); 
displayMatrix(result, rows1, cols2); 
return 0; 
} 
OUTPUT:- 
Enter the number of rows and columns for Matrix 1: 2 2 
Enter the number of rows and columns for Matrix 2: 2 2 
Enter elements of Matrix 1 (2 x 2): 
3  7 
4  9 
Enter elements of Matrix 2 (2 x 2): 
6  2 
5  8 
Resultant Matrix (2 x 2): 
53  62 
69  80 -------------------------------- 
Process exited after 41.32 seconds with return value 0 
Press any key to continue . . . 
Enter the number of rows and columns for Matrix 1: 3 3 
Enter the number of rows and columns for Matrix 2: 3 3 
Enter elements of Matrix 1 (3 x 3): 
12 8   4 
3 17 14 
9   8   10 
Enter elements of Matrix 2 (3 x 3): 
5 19 3 
6 15 9 
7 8 16 
Resultant Matrix (3 x 3): 
136 380 172 
215 424 386 
163 371 259 
 -------------------------------- 
Process exited after 57.31 seconds with return value 0 
Press any key to continue . . . 
 
 
 
Program 5 555555555555555555555555555555555555555----------------------------------------------------------------------------------------------

An electricity board charges the following rates for the use of electricity: for the first 200 units 
80 paise per unit:for the next 100 units 90 paise per unit: beyond 300 units Rs 1 per unit. All 
users are charged a minimum of Rs.100 as meter charge. If the total amount is more than Rs 
400, then an additional surcharge of 15% of total amount is charged. Write a program to read 
the name of the user, number of units consumed and print out the charges. 
 
#include <stdio.h> 
 
int main() { 
    char name[50];    // To store the user's name 
    int units;        // To store the number of units consumed 
    float totalAmount = 0.0, surcharge = 0.0; 
 
    // Reading the name of the user 
    printf("Enter the name of the user: "); 
    fgets(name, sizeof(name), stdin);  // Using fgets to allow spaces in the name 
 
    // Reading the number of units consumed 
    printf("Enter the number of units consumed: "); 
    scanf("%d", &units); 
 
    // Initial charge is Rs. 100 (minimum charge) 
    totalAmount = 100.0; 
 
    // Calculate charges based on units consumed 
    if (units <= 200) { 
        // For the first 200 units, 80 paise per unit 
        totalAmount += units * 0.80; 
    } else if (units <= 300) { 
        // For the first 200 units, 80 paise per unit 
        totalAmount += 200 * 0.80; 
        // For the next 100 units, 90 paise per unit 
        totalAmount += (units - 200) * 0.90; 
    } else { 
        // For the first 200 units, 80 paise per unit 
        totalAmount += 200 * 0.80; 
        // For the next 100 units, 90 paise per unit 
        totalAmount += 100 * 0.90; 
        // For units beyond 300, Rs. 1 per unit 
        totalAmount += (units - 300) * 1.0; 
    } 
 
    // If the total amount is more than Rs. 400, apply surcharge 
    if (totalAmount > 400) { 
        surcharge = totalAmount * 0.15;  // 15% surcharge 
        totalAmount += surcharge;         // Adding surcharge to the total amount 
    } 
 
    // Print the charges 
    printf("\nElectricity Bill for %s", name); 
    printf("Units Consumed: %d\n", units); 
    printf("Total Charge: Rs. %.2f\n", totalAmount); 
    printf("Surcharge: Rs. %.2f\n", surcharge); 
 
    return 0; 
} 
 
OUTPUT:-  
Enter the name of the user: Ajay 
Enter the number of units consumed: 100 
 
Electricity Bill for Ajay 
Units Consumed: 100 
Total Charge: Rs. 180.00 
Surcharge: Rs. 0.00 
 -------------------------------- 
Process exited after 10.32 seconds with return value 0 
Press any key to continue . . . 
 
 
Program 6666666666666---------------------------------------------------------------------------------------------

Write functions to implement string operations such as compare, concatenate, and find string 
length. Use the parameter passing techniques. 
 
#include <stdio.h> 
 
// Function to find the length of a string 
int stringLength(char str[]) { 
    int length = 0; 
    while (str[length] != '\0') { 
        length++; 
    } 
    return length; 
} 
 
// Function to compare two strings (returns 0 if equal, negative/positive value if not) 
int stringCompare(char str1[], char str2[]) { 
    int i = 0; 
    while (str1[i] != '\0' && str2[i] != '\0') { 
        if (str1[i] != str2[i]) { 
            return str1[i] - str2[i]; // return difference 
        } 
        i++; 
    } 
    return str1[i] - str2[i];  // handles different lengths if strings are equal up to the null character 
} 
 
// Function to concatenate two strings 
void stringConcatenate(char str1[], char str2[], char result[]) { 
    int i = 0, j = 0; 
 
    // Copy the first string into result 
    while (str1[i] != '\0') { 
        result[i] = str1[i]; 
        i++; 
    } 
 
    // Concatenate the second string to result 
    while (str2[j] != '\0') { 
        result[i + j] = str2[j]; 
        j++; 
    } 
 
    // Null-terminate the result string 
    result[i + j] = '\0'; 
} 
 
int main() { 
    char str1[100], str2[100], result[200]; 
    int choice, len; 
 
    // Input strings 
    printf("Enter first string: "); 
    fgets(str1, sizeof(str1), stdin); 
    printf("Enter second string: "); 
    fgets(str2, sizeof(str2), stdin); 
 
    // Remove newline characters if any 
    str1[strcspn(str1, "\n")] = '\0'; 
    str2[strcspn(str2, "\n")] = '\0'; 
 
    printf("\nSelect an operation:\n"); 
    printf("1. Compare strings\n"); 
    printf("2. Concatenate strings\n"); 
    printf("3. Find length of a string\n"); 
    printf("Enter your choice (1-3): "); 
    scanf("%d", &choice); 
 
    switch (choice) { 
        case 1: 
            // Compare two strings 
            if (stringCompare(str1, str2) == 0) { 
                printf("The strings are equal.\n"); 
            } else { 
                printf("The strings are not equal.\n"); 
            } 
            break; 
 
        case 2: 
            // Concatenate two strings 
            stringConcatenate(str1, str2, result); 
            printf("Concatenated string: %s\n", result); 
            break; 
 
        case 3: 
            // Find length of the first string 
            len = stringLength(str1); 
            printf("Length of the first string is: %d\n", len); 
            break; 
 
        default: 
            printf("Invalid choice!\n"); 
            break; 
    } 
 
    return 0; 
} 
 
OUTPUT:- 
 
Enter first string: hello 
Enter second string: world 
 
Select an operation: 
1. Compare strings 
2. Concatenate strings 
3. Find length of a string 
Enter your choice (1-3): 1 
The strings are not equal. -------------------------------- 
Process exited after 10.36 seconds with return value 0 
Press any key to continue . . . 
Enter first string: hello world 
Enter second string: program 
Select an operation: 
1. Compare strings 
2. Concatenate strings 
3. Find length of a string 
Enter your choice (1-3): 2 
Concatenated string: hello worldprogram -------------------------------- 
Process exited after 22.34 seconds with return value 0 
Press any key to continue . . . 
Enter first string: Constant 
Enter second string: Parameter 
Select an operation: 
1. Compare strings 
2. Concatenate strings 
3. Find length of a string 
Enter your choice (1-3): 3 
Length of the first string is: 8 -------------------------------- 
Process exited after 15.67 seconds with return value 0 
Press any key to continue . . . 
 
 
7.Implement structures to read, write and compute average- marks of the students, list the students 
scoring above and below the average marks for a class of N students.-------------------------------------------------------------------------------------------------------


 #include <stdio.h>
 #include <stdio.h>
 #define MAX_NAME_LEN 100
 // Structure to store student name and marks
 struct Student {
    char name[MAX_NAME_LEN];
    float marks;
 };
 // Function to compute the average marks
 float compute_average(struct Student students[], int n) {
    float sum = 0.0;
    int i;
    for (i = 0; i < n; i++) {
        sum += students[i].marks;
    }
    return sum / n;
 }
 // Function to print students with marks above the average
 void print_above_average(struct Student students[], int n, float average) 
{
 int i;
    printf("\nStudents who scored above the average (%.2f):\n", average);
    for ( i = 0; i < n; i++) {
        if (students[i].marks > average) {
            printf("%s: %.2f\n", students[i].name, students[i].marks);
        }
    }
 }
 // Function to print students with marks below the average
 void print_below_average(struct Student students[], int n, float average)
 {
 }
 int i;
    printf("\nStudents who scored below the average (%.2f):\n", average);
    for (i = 0; i < n; i++) {
        if (students[i].marks < average) {
            printf("%s: %.2f\n", students[i].name, students[i].marks);
        }
    }
 int main() {
    int N,i;
    // Read number of students
    printf("Enter the number of students: ");
    scanf("%d", &N);
    struct Student students[N];
    // Read student data
    for ( i = 0; i < N; i++) {
        printf("Enter name of student %d: ", i + 1);
        getchar();  // To consume any leftover newline character
        fgets(students[i].name, MAX_NAME_LEN, stdin);
        // Remove newline character from the name
        students[i].name[strcspn(students[i].name, "\n")] = 0;
        printf("Enter marks for %s: ", students[i].name);
        scanf("%f", &students[i].marks);
    }
    // Compute the average marks
    float average = compute_average(students, N);
    // Print the average marks
    printf("\nThe average marks of the class are: %.2f\n", average);
    // Print students above and below average
    print_above_average(students, N, average);
    print_below_average(students, N, average);
    return 0;
 }
 
8th  question-------------------------------------------------------------------------------------------------------------------------------------

#include<stdio.h> 
 
void copyFile(const char *sourceFile, const char *targetFile) 
{ 
    FILE *source, *target; 
    char ch; 
    source = fopen(sourceFile, "r"); 
    if(source == NULL) 
    { 
        printf("ERROR: cannot open %s\n", sourceFile); 
        return; 
    } 
     
    target = fopen(targetFile, "w"); 
    if(source == NULL) 
    { 
        printf("ERROR: cannot open %s\n", targetFile); 
        fclose(source); 
        return; 
    } 
 
    while((ch = fgetc(source)) != EOF) 
    { 
        fputc(ch, target); 
    } 
printf("File copied successfully from %s to %s\n", sourceFile, targetFile); 
fclose(source); 
fclose(target); 
} 
int main() 
{ 
} 
char sourceFile[100], targetFile[100]; 
printf("Enter the name of the input file: "); 
scanf("%s", sourceFile); 
printf("Enter the name of the output file: "); 
scanf("%s", targetFile); 
copyFile(sourceFile, targetFile); 
return 0; 
