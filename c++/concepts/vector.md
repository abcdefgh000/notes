# Vector

# Vector of vectors

A vector of vectors is like a grid, each row in this grid is a vector. Each row (vector) in this grid can have differenct length!

To instantiate a vector of vectors that all rows in it has the same length:

```cpp
// In this vector of vectors, there are 3 "rows", namely 3 vectors,
// each vector has a length of 5, 
// and all the elements in each vector has an initial value of 1
vector< vector<int> > grid(3, vector<int>(5, 1));

```

```cpp
	grid[1].push_back(8);

	for(int row=0; row < grid.size(); row++) {
			for(int col=0; col < grid[row].size(); col++) {
				cout << grid[row][col] << flush;
			}

			cout << endl;
	}
```
