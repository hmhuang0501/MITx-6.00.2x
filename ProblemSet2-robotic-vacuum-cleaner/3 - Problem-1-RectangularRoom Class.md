### Problem 1: RectangularRoom Class 
10.0/10.0 points (graded) 

You will need to design two classes to keep track of which parts of the room have been cleaned as well as the position and direction of each robot.

In *ps2.py*, we've provided skeletons for the following two classes, which you will fill in in Problem 1:

 * `RectangularRoom`: Represents the space to be cleaned and keeps track of which tiles have been cleaned.
 * `Position`: We've also provided a complete implementation of this class. It stores the x- and y-coordinates of a robot in a room.

Read *ps2.py* carefully before starting, so that you understand the provided code and its capabilities. 


In this problem you will implement the `RectangularRoom` class. For this class, decide what fields you will use and decide how the following operations are to be performed:

+ Initializing the object 
+ Marking an appropriate tile as cleaned when a robot moves to a given position (casting floats to ints - and/or the function `math.floor` - may be useful to you here) 
+ Determining if a given tile has been cleaned 
+ Determining how many tiles there are in the room 
+ Determining how many cleaned tiles there are in the room 
+ Getting a random position in the room 
+ Determining if a given position is in the room 

Complete the `RectangularRoom` class by implementing its methods in *ps2.py*.

Although this problem has many parts, it should not take long once you have chosen how you wish to represent your data. For reasonable representations, *a majority of the methods will require only a couple of lines of code*.

**Hint**: During debugging, you might want to use `random.seed(0)` so that your results are reproducible.

Enter your code for `RectangularRoom` below.

```python
class RectangularRoom(object):

    """
    A RectangularRoom represents a rectangular region containing clean or dirty tiles.

    A room has a width and a height and contains (width * height) tiles.
    At any particular time, each of these tiles is either clean or dirty.
    """

    def __init__(self, width, height):
        """
        Initializes a rectangular room with the specified width and height.

        Initially, no tiles in the room have been cleaned.

        width: an integer > 0
        height: an integer > 0
        """
        self.width = width
        self.height = height
        
        #self.tiles = {}
        #for i in range(self.width):
        #    for j in range(self.height):
        #        self.tiles[(i,j)] = False
        self.tiles = { (i,j) : False for i in range(self.width) for j in range(self.height) }        

    def cleanTileAtPosition(self, pos : Position):
        """
        Mark the tile under the position POS as cleaned.

        Assumes that POS represents a valid position inside this room.

        pos: a Position
        """
        self.tiles[ (math.floor(pos.getX()), math.floor(pos.getY())) ] = True

    def isTileCleaned(self, m, n):
        """
        Return True if the tile (m, n) has been cleaned.

        Assumes that (m, n) represents a valid tile inside the room.

        m: an integer
        n: an integer

        returns: True if (m, n) is cleaned, False otherwise
        """
        return self.tiles[(m,n)]
    
    def getNumTiles(self):
        """
        Return the total number of tiles in the room.

        returns: an integer
        """
        return self.width * self.height

    def getNumCleanedTiles(self):
        """
        Return the total number of clean tiles in the room.

        returns: an integer
        """
        cleaned_tiles = [ status for status in self.tiles.values() if status is True ]
        return len(cleaned_tiles)

    def getRandomPosition(self):
        """
        Return a random position inside the room.

        returns: a Position object.
        """
        return Position( random.uniform(0, self.width), random.uniform(0, self.height) )

    def isPositionInRoom(self, pos : Position):
        """
        Return True if pos is inside the room.

        pos: a Position object.

        returns: True if pos is in the room, False otherwise.
        """
        # if ( (0 <= pos.getX() < self.width) and (0 <= pos.getY() < self.height) ):
        #     return True
        # else:
        #     return False
        return True if (0 <= pos.getX() < self.width) and (0 <= pos.getY() < self.height) else False
```