#include <stdio.h>
#include <stdlib.h>
#define MEMORY_SIZE 100
struct Block {
    int size;
    int free;
};
struct Block memory[MEMORY_SIZE];
void initializeMemory() {
    memory[0].size = MEMORY_SIZE - sizeof(struct Block);
    memory[0].free = 1;
}
void splitBlock(int index, int size) {
    memory[index + size].size = memory[index].size - size - sizeof(struct Block);
    memory[index + size].free = 1;
    memory[index].size = size;
    memory[index].free = 0;
}
void allocateMemoryFirstFit(int size) {
    for (int i = 0; i < MEMORY_SIZE; ++i) {
        if (memory[i].free && memory[i].size >= size) {
            splitBlock(i, size);
            printf("Memory allocated using First Fit, starting index: %d\n", i);
            return;
        }
    }
    printf("Memory allocation using First Fit failed: Not enough space available.\n");
}
void allocateMemoryBestFit(int size) {
    int bestFitIndex = -1;
    int minFreeSpace = MEMORY_SIZE + 1;
    for (int i = 0; i < MEMORY_SIZE; ++i) {
        if (memory[i].free && memory[i].size >= size && memory[i].size - size < minFreeSpace) {
            bestFitIndex = i;
            minFreeSpace = memory[i].size - size;
        }
    }
    if (bestFitIndex != -1) {
        splitBlock(bestFitIndex, size);
        printf("Memory allocated using Best Fit, starting index: %d\n", bestFitIndex);
    } else {
        printf("Memory allocation using Best Fit failed: Not enough space available.\n");
    }
}
void allocateMemoryWorstFit(int size) {
    int worstFitIndex = -1;
    int maxFreeSpace = -1;
    for (int i = 0; i < MEMORY_SIZE; ++i) {
        if (memory[i].free && memory[i].size >= size && memory[i].size - size > maxFreeSpace) {
            worstFitIndex = i;
            maxFreeSpace = memory[i].size - size;
        }
    }
    if (worstFitIndex != -1) {
        splitBlock(worstFitIndex, size);
        printf("Memory allocated using Worst Fit, starting index: %d\n", worstFitIndex);
    } else {
        printf("Memory allocation using Worst Fit failed: Not enough space available.\n");
    }
}
void deallocateMemory(int index) {
    memory[index].free = 1;
    while (index < MEMORY_SIZE - 1 && memory[index + 1].free) {
        memory[index].size += memory[index + 1].size + sizeof(struct Block);
        ++index;
    }
    while (index > 0 && memory[index - 1].free) {
        memory[index - 1].size += memory[index].size + sizeof(struct Block);
        --index;
    }
    printf("Memory deallocated starting from index %d\n", index);
}
int main() {
    initializeMemory();
    allocateMemoryFirstFit(20);
    allocateMemoryBestFit(15);
    allocateMemoryWorstFit(25);
    deallocateMemory(0);
    return 0;
}
