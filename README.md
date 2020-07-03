# About
This respository demonstrates an algorithm for solving Minesweeper. The algorithm and the internal game of Minesweeper used to test the algorithm are based on the version of the game packaged with Windows XP.

# Board Generation
Boards are generated using the C++ STL Mersenne Twister pseudorandom number generator. After the first move is made, board cells are randomly chosen until the desired number of mines is met. A mine is placed in a randomly chose board cell if they are not the location of the first move and they do not already hold a mine.

# Solving Algorithm
The algorithm first tries to determine a guaranteed safe move based on logic. If no such move is available, it uses probability to select the safest possible move.

## Logic
Guaranteed safe moves can be determined by analyzing the relationship between hint cells and their adjacent covered cells (frontier cells). The algorithm does this by creating a matrix, where each column represents a frontier cell and each row represents a hint cell. The interesections between the rows and columns are 1 if a hint cell is adjacent to a particular frontier cell and 0 if otherwise. The last column of the matrix is filled with the actual hint values corresponding to the hint cells represented by each row.

This matrix is then converted to its row echelon form. If there exists a row in the converted matrix that contains only a single non-zero entry besides the last column and that entry is a 0, then the corresponding cell is safe. If the entry is a 1, the corresponding cell is a mine. Also, if there exists a row where the last column is 0, then all columns in that row that have an entry of 1 correspond to a safe cell.

Using this method, the solver can deduce which cells are safe and which are mines and make move accordingly until the point comes where a guess must be made.

## Probability
If no guaranteed safe move can be found, then we find the saf*est* move.
