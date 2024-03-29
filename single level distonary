#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_FILES 100
#define MAX_FILENAME_LENGTH 50

struct File {
    char name[MAX_FILENAME_LENGTH];
};

struct File directory[MAX_FILES];
int fileCount = 0;

void createFile(const char *filename) {
    if (fileCount < MAX_FILES) {
        strcpy(directory[fileCount].name, filename);
        fileCount++;
        printf("File '%s' created successfully.\n", filename);
    } else {
        printf("Cannot create file '%s'. Directory is full.\n", filename);
    }
}

void deleteFile(const char *filename) {
    int found = 0;
    for (int i = 0; i < fileCount; ++i) {
        if (strcmp(directory[i].name, filename) == 0) {
            found = 1;
            for (int j = i; j < fileCount - 1; ++j) {
                strcpy(directory[j].name, directory[j + 1].name);
            }
            fileCount--;
            printf("File '%s' deleted successfully.\n", filename);
            break;
        }
    }
    if (!found) {
        printf("File '%s' not found.\n", filename);
    }
}

void listFiles() {
    printf("Files in the directory:\n");
    for (int i = 0; i < fileCount; ++i) {
        printf("%s\n", directory[i].name);
    }
}

int main() {
    int choice;
    char filename[MAX_FILENAME_LENGTH];

    do {
        printf("\nMenu:\n");
        printf("1. Create File\n");
        printf("2. Delete File\n");
        printf("3. List Files\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter filename: ");
                scanf("%s", filename);
                createFile(filename);
                break;
            case 2:
                printf("Enter filename to delete: ");
                scanf("%s", filename);
                deleteFile(filename);
                break;
            case 3:
                listFiles();
                break;
            case 4:
                printf("Exiting program.\n");
                break;
            default:
                printf("Invalid choice. Please try again.\n");
        }
    }
	while (choice != 4);
    return 0;
}
