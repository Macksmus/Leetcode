```c
//leetcode problem 1267. Count Servers that Communicate

int isIsolated(int** grid, int gridSize, int* gridColSize, int row, int column){
    for(int i = 0; i < gridSize; i++){
        if(grid[i][column] == 1 && i != row){ //checking for each row of the array at the given column number to find overlap (e.g. if the computer is at (2,2) checks (0,2),(1,2),etc.)
            return 0;
        }
    }
    for(int j = 0; j <gridColSize[0]; j++){
        if(grid[row][j] == 1 && j != column){ //checking for each column of the array at the given row number to find overlap (e.g. if the computer is at (3,3) checks (3,0),(3,1), etc.)
            return 0; 
        }
    }
    return 1;
}


int countServers(int** grid, int gridSize, int* gridColSize) {
    int counter = 0;
    for(int i = 0; i < gridSize; i++){
        for(int j = 0; j < gridColSize[i]; j++){
            if(grid[i][j] == 0){ //checking if there's a computer at the given point.
                continue;
            }
            if(isIsolated(grid,gridSize,gridColSize, i, j) == 0) //if the isIsolated function returns 0, that means it's not isolated and adds to the counter communicating servers.
                counter++;
        }
    }
    return counter;
}
```
