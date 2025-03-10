1--------------------------------------------------------------------------------------------------------------- 
 
#include <stdio.h> 
 
int main() { 
  double num1, num2; 
  char operator; 
 
  printf("Simple Calculator\n"); 
  printf("====================\n"); 
  printf("Choose an operator (+, -, *, /): "); 
  scanf(" %c", &operator); 
 
  printf("Enter the first number: "); 
  scanf("%lf", &num1); 
  printf("Enter the second number: "); 
  scanf("%lf", &num2); 
 
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
      if (num2 != 0) 
   { 
        printf("%.2lf / %.2lf = %.2lf\n", num1, num2, num1 / num2); 
      } else  
   { 
        printf("Error! Division by zero.\n"); 
      } 
      break; 
    default: 
      printf("Invalid operator! Please use one of the following: +, -, *, /\n"); 
      break; 
  } 
  return 0; 
} 
 
 
2---------------------------------------------------------------------- 
#include <stdio.h> 
 
int binarySearch(int arr[], int size, int target)  
{ 
  int left = 0, right = size - 1; 
  while (left <= right)  
  { 
    int mid = left + (right - left) / 2; 
    if (arr[mid] == target) 
 { 
      return mid; 
    } 
    if (arr[mid] < target)  
 { 
      left = mid + 1; 
    }  
 else  
 { 
      right = mid - 1; 
    } 
  } 
  return -1; 
} 
 
int main() { 
  int arr[] = {2, 5, 8, 12, 16, 23, 42, 56, 67, 89}; 
  int size = sizeof(arr) / sizeof(arr[0]); 
  int target; 
 
  printf("Enter the number to search: "); 
  scanf("%d", &target); 
 
  int result = binarySearch(arr, size, target); 
 
  if (result != -1) { 
    printf("Element %d found at index %d.\n", target, result); 
  } else { 
    printf("Element %d not found in the array.\n", target); 
  } 
  return 0; 
} 
3---------------------------------------------------------------------- 
 
#include <stdio.h> 
 
void bubbleSort(int arr[], int size)  
{ 
  int i, j, temp; 
  for (i = 0; i < size - 1; i++)  
  { 
    for (j = 0; j < size - 1 - i; j++)  
 { 
      if (arr[j] > arr[j + 1])  
   { 
        temp = arr[j]; 
        arr[j] = arr[j + 1]; 
        arr[j + 1] = temp; 
      } 
    } 
  } 
} 
 
void printArray(int arr[], int size) { 
 int i; 
  for (i = 0; i < size; i++) { 
    printf("%d ", arr[i]); 
  } 
  printf("\n"); 
} 
 
int main() { 
int N, i; 
printf("Enter the number of elements: "); 
scanf("%d", &N); 
int arr[N]; 
printf("Enter the elements: \n"); 
for (i = 0; i < N; i++) { 
scanf("%d", &arr[i]); 
} 
printf("\nArray before sorting:\n"); 
printArray(arr, N); 
bubbleSort(arr, N); 
printf("\nArray after sorting:\n"); 
printArray(arr, N); 
return 0; 
} 
4----------------------------------------------- 
#include <stdio.h> 
int validateMultiplication(int rows1, int cols1, int rows2, int cols2)  
{ 
if (cols1 != rows2) { 
printf("Matrix multiplication not possible. Number of columns in Matrix 1 (%d) must be 
equal to the number of rows in Matrix 2 (%d).\n", cols1, rows2); 
    return 0; 
  } 
  return 1; 
} 
 
void multiplyMatrices(int mat1[10][10], int mat2[10][10], int result[10][10], int rows1, int 
cols1, int rows2, int cols2)  
{ 
  int i, j, k; 
  for (i = 0; i < rows1; i++)  
  { 
    for (j = 0; j < cols2; j++)  
 { 
      result[i][j] = 0; 
      for (k = 0; k < cols1; k++)  
   { 
        result[i][j] += mat1[i][k] * mat2[k][j]; 
      } 
    } 
  } 
} 
 
void displayMatrix(int matrix[10][10], int rows, int cols)  
{ 
  int i, j; 
  for (i = 0; i < rows; i++)  
  { 
    for (j = 0; j < cols; j++)  
 { 
      printf("%d ", matrix[i][j]); 
    } 
    printf("\n"); 
  } 
} 
 
int main() { 
  int mat1[10][10], mat2[10][10], result[10][10]; 
  int rows1, cols1, rows2, cols2, i, j; 
 
  printf("Enter the number of rows and columns for Matrix 1: \n"); 
  scanf("%d %d", &rows1, &cols1); 
 
  printf("Enter the number of rows and columns for Matrix 2: \n"); 
  scanf("%d %d", &rows2, &cols2); 
 
  if (!validateMultiplication(rows1, cols1, rows2, cols2))  
  { 
    return 0; 
  } 
 
  printf("Enter elements of Matrix 1 (%d x %d):\n", rows1, cols1); 
  for (i = 0; i < rows1; i++)  
  { 
    
    for (j = 0; j < cols1; j++)  
 { 
      scanf("%d", &mat1[i][j]); 
      
    } 
} 
printf("Enter elements of Matrix 2 (%d x %d):\n", rows2, cols2); 
for (i = 0; i < rows2; i++)  
{ 
} 
for (j = 0; j < cols2; j++)  
{ 
scanf("%d", &mat2[i][j]); 
} 
multiplyMatrices(mat1, mat2, result, rows1, cols1, rows2, cols2); 
printf("Resultant Matrix (%d x %d):\n", rows1, cols2); 
displayMatrix(result, rows1, cols2); 
return 0; 
} 
5----------------------------------------------------------------------------------- 
#include <stdio.h> 
int main() { 
char name[50]; 
int units; 
f
 loat totalAmount = 0.0, surcharge = 0.0; 
printf("Enter the name of the user: "); 
  fgets(name, sizeof(name), stdin); 
 
  printf("Enter the number of units consumed: "); 
  scanf("%d", &units); 
 
  totalAmount = 100.0; 
 
  if (units <= 200) { 
    totalAmount += units * 0.80; 
  } else if (units <= 300) { 
    totalAmount += 200 * 0.80; 
    totalAmount += (units - 200) * 0.90; 
  } else { 
    totalAmount += 200 * 0.80; 
    totalAmount += 100 * 0.90; 
    totalAmount += (units - 300) * 1.0; 
  } 
 
  if (totalAmount > 400) { 
    surcharge = totalAmount * 0.15; 
    totalAmount += surcharge; 
  } 
 
  printf("\nElectricity Bill for %s", name); 
  printf("Units Consumed: %d\n", units); 
  printf("Total Charge: Rs. %.2f\n", totalAmount); 
  printf("Surcharge: Rs. %.2f\n", surcharge); 
 
  return 0; 
} 
 
6----------------------------------------------------------------------------------- 
 
#include <stdio.h> 
#include <string.h> 
 
int stringLength(char str[]) { 
  int length = 0; 
  while (str[length] != '\0') { 
    length++; 
  } 
  return length; 
} 
 
int stringCompare(char str1[], char str2[]) { 
  int i = 0; 
  while (str1[i] != '\0' && str2[i] != '\0') { 
    if (str1[i] != str2[i]) { 
      return str1[i] - str2[i]; 
    } 
    i++; 
  } 
  return str1[i] - str2[i]; 
} 
 
void stringConcatenate(char str1[], char str2[], char result[]) { 
  int i = 0, j = 0; 
  while (str1[i] != '\0') { 
result[i] = str1[i]; 
i++; 
} 
while (str2[j] != '\0') { 
result[i + j] = str2[j]; 
j++; 
} 
result[i + j] = '\0'; 
} 
int main() { 
char str1[100], str2[100], result[200]; 
int choice, len; 
printf("Enter first string: "); 
fgets(str1, sizeof(str1), stdin); 
printf("Enter second string: "); 
fgets(str2, sizeof(str2), stdin); 
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
      if (stringCompare(str1, str2) == 0) { 
        printf("The strings are equal.\n"); 
      } else { 
        printf("The strings are not equal.\n"); 
      } 
      break; 
    case 2: 
      stringConcatenate(str1, str2, result); 
      printf("Concatenated string: %s\n", result); 
      break; 
    case 3: 
      len = stringLength(str1); 
      printf("Length of the first string is: %d\n", len); 
      break; 
    default: 
      printf("Invalid choice!\n"); 
      break; 
  } 
 
  return 0; 
} 
 
7------------------------------------------------------------------------------------ 
 
 
#include <stdio.h> 
#include <string.h> 
 
#define MAX_NAME_LEN 100 
 
struct Student { 
    char name[MAX_NAME_LEN]; 
    float marks; 
}; 
 
float compute_average(struct Student students[], int n) { 
    float sum = 0.0; 
    int i; 
    for (i = 0; i < n; i++) { 
        sum += students[i].marks; 
    } 
    return sum / n; 
} 
 
void print_above_average(struct Student students[], int n, float average) { 
    int i; 
    printf("\nStudents who scored above the average (%.2f):\n", average); 
    for (i = 0; i < n; i++) { 
        if (students[i].marks > average) { 
            printf("%s: %.2f\n", students[i].name, students[i].marks); 
        } 
    } 
} 
 
void print_below_average(struct Student students[], int n, float average) { 
    int i; 
    printf("\nStudents who scored below the average (%.2f):\n", average); 
    for (i = 0; i < n; i++) { 
        if (students[i].marks < average) { 
            printf("%s: %.2f\n", students[i].name, students[i].marks); 
        } 
    } 
} 
 
int main() { 
    int N, i; 
 
    printf("Enter the number of students: "); 
    scanf("%d", &N); 
 
    struct Student students[N]; 
 
    for (i = 0; i < N; i++) { 
        printf("Enter name of student %d: ", i + 1); 
        getchar(); 
        fgets(students[i].name, MAX_NAME_LEN, stdin); 
        students[i].name[strcspn(students[i].name, "\n")] = 0; 
        printf("Enter marks for %s: ", students[i].name); 
        scanf("%f", &students[i].marks); 
    } 
 
    float average = compute_average(students, N); 
 
    printf("\nThe average marks of the class are: %.2f\n", average); 
 
    print_above_average(students, N, average); 
    print_below_average(students, N, average); 
 
    return 0; 
} 
 
8----------------------------------------------------------------------------------- 
 
 
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
