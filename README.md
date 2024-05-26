# DegreesOfSeparationBFS

The `DegreesOfSeparationBFS` class provides a client for finding the degree of separation between one distinguished individual and every other individual in a social network. For example, if the social network consists of actors connected by their appearances in the same movie, this class can compute the "Kevin Bacon number" for each actor.

## Features

- Computes degrees of separation using breadth-first search (BFS).
- Determines the path between two individuals in the network.
- Uses a symbol graph to map names to indices and vice versa.
- Provides methods to print the path and the degree of separation.

## Requirements

This class depends on the following libraries from the [algs4](https://algs4.cs.princeton.edu/code/) package by Robert Sedgewick and Kevin Wayne:
- `edu.princeton.cs.algs4.Stack`
- `edu.princeton.cs.algs4.SymbolGraph`
- `edu.princeton.cs.algs4.BreadthFirstPaths`

Ensure you have the `algs4.jar` file in your classpath.

## Usage

### Command Line

To run this program from the command line, use the following command:

```sh
java DegreesOfSeparationBFS <filename> <delimiter> <source> [<sink>...]
```

- `<filename>`: Path to the file containing the network data.
- `<delimiter>`: The delimiter used in the file to separate the entities.
- `<source>`: The name of the distinguished individual (e.g., Kevin Bacon).
- `[<sink>...]`: (Optional) List of names to compute degrees of separation and paths from the source.

### Example

```sh
java DegreesOfSeparationBFS movies.txt "/" "Bacon, Kevin"
```

This example calculates the degrees of separation for Kevin Bacon based on the data in `movies.txt`.

### Methods

- `int baconNumber(String sink)`: Returns the degree of separation (Bacon number) for the specified individual.
- `Stack<Integer> graphPath(String sink)`: Returns the path from the source to the specified individual as a stack of integers.
- `void printPath(Stack<Integer> path)`: Prints the path from the source to the specified individual.

## Example Code

Here's an example of how to use the `DegreesOfSeparationBFS` class in a Java program:

```java
public static void main(String[] args) {
    String filename = args[0];
    String delimiter = args[1];
    String source = args[2];

    DegreesOfSeparationBFS baconGraph = new DegreesOfSeparationBFS(filename, delimiter, source);

    for (int i = 3; i < args.length; i++) {
        int baconNumber = baconGraph.baconNumber(args[i]);
        System.out.println("Degree of separation to " + args[i] + ": " + baconNumber);

        Stack<Integer> path = baconGraph.graphPath(args[i]);
        baconGraph.printPath(path);
    }
}
```

## License

This code is part of `algs4.jar`, which is free software under the GNU General Public License. For more details, see [GNU General Public License](http://www.gnu.org/licenses).