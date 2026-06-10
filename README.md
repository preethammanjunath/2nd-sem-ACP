1.Add object
a. Parameter Definition: The process begins by capturing the desired shape type from the user,
which determines which set of geometric inputs—such as endpoint coordinates for lines or center and radius for circles—are required.
This step ensures that every shape is correctly identified by a kind tag before storage.
b. Array Storage: The gathered data is encapsulated into a struct shape object, which is then placed into the next available slot in
the global obj array. Once the data is stored, the total counter is incremented, effectively finalizing the object's inclusion in the rendering
pipeline for future display.

2.Delete object
a. Index Validation: When a deletion is requested, the program first verifies that the chosen index exists within the current bounds of the obj array,
preventing memory errors or invalid operations. This check ensures that only active shapes are targeted for removal.
b. Array Reorganization: Upon validation, the program performs an "in-place" shift by moving all subsequent objects one position forward,
which effectively overwrites the deleted data and closes the gap in the array. Finally, the total count is decremented to reflect the reduced 
number of shapes currently available in the system.

3.List objects
a. Iterative Traversal: The program performs a sequential loop through the obj array, starting from the first element and proceeding up to the current total count of stored shapes.
This ensures that every object currently managed by the editor is processed.
b. Formatted Reporting: For every index, the program reads the kind integer and prints a descriptive summary of the shape's specific coordinates or
radius to the terminal. This provides the user with a clear, text-based overview of the scene, making it easy to identify which indices correspond to which 
shapes for future modification or deletion tasks.

4.Modify object
a. Retrieval and Access: When the user enters an index to modify, the program validates the input against the current total count to ensure it points to a valid memory
location within the obj array. Once verified, it provides the user with the opportunity to overwrite the existing struct data by re-entering the shape type and its corresponding geometric parameters.
b. Data Update: Upon receiving the new values, the program performs an assignment operation to replace the old structure at that specific index,
ensuring that the next time the render() function is called, the canvas will reflect the updated shape geometry rather than the previous state.

5.Display picture
a. Canvas Initialization: The process begins by flushing the entire 80x24 character grid, resetting every cell to an underscore character to provide a
clean slate for the drawing operations. This ensures that no remnants of previous renders interfere with the current output.
b. Rasterization Pipeline: The program then iterates through the active obj array, passing each shape's parameters into its respective
mathematical algorithm, such as Bresenham’s, which calculates the specific pixel coordinates to be colored with an asterisk on the canvas grid.
