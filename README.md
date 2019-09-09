# Danske-Bank
Exercise

using System;
					
public class Program
{
	int count=0;
	int highestSum=0;
	int[] path= new int [15];
	int[] highestPath= new int [15];

	int[][] inputGraph = new int[][] 
	{
    	new int[] {215},
	new int[] {192, 124},
        new int[] {117, 269, 442},
        new int[] {218, 836, 347, 235},
        new int[] {320, 805, 522, 417, 345},
        new int[] {229, 601, 728, 835, 133, 124},
        new int[] {248, 202, 277, 433, 207, 263, 257},
        new int[] {359, 464, 504, 528, 516, 716, 871, 182},
        new int[] {461, 441, 426, 656, 863, 560, 380, 171, 923},
        new int[] {381, 348, 573, 533, 448, 632, 387, 176, 975, 449},
        new int[] {223, 711, 445, 645, 245, 543, 931, 532, 937, 541, 444},
        new int[] {330, 131, 333, 928, 376, 733, 017, 778, 839, 168, 197, 197},
        new int[] {131, 171, 522, 137, 217, 224, 291, 413, 528, 520, 227, 229, 928},
        new int[] {223, 626, 034, 683, 839, 052, 627, 310, 713, 999, 629, 817, 410, 121},
        new int[] {924, 622, 911, 233, 325, 139, 721, 218, 253, 223, 107, 233, 230, 124, 233}
	};
	

	public void addNextChild(int row, int column)
	{
		path[row]=inputGraph[row][column];
		
		//if next row does not exist, than count if the path has the highest sum
		if (row+1>=15)  
		{
			count=0;
			for(int i=0; i<path.Length;i++)
			{
				count+=path[i];
			}
			if(count>highestSum)
			{
				path.CopyTo(highestPath,0);
				highestSum=count;
			}
			return;
		}
		
		//Child 1
		//is child Valid, true if child changes odd vs even from parent
		if (/*parent*/(inputGraph[row][column]%2) != /*child*/(inputGraph[row+1][column] %2))
		{
			addNextChild(row+1, column);
		}
		
		//Child 2
		//is child Valid, true if child changes odd vs even from parent
		if (/*parent*/(inputGraph[row][column]%2) != /*child*/(inputGraph[row+1][column+1] %2))
		{
			addNextChild(row+1, column+1);
		}
	}
	
	public void Main()
	{
		addNextChild(0,0);	
		Console.WriteLine("The highest sum is "+ highestSum);
		Console.Write("From the path of ");
		for(int i=0; i<highestPath.Length;i++)
		{
			Console.Write(highestPath[i]+" ");
		}	
	}
}

	
