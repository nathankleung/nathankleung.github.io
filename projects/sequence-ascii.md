---
layout: project
type: project
image: img/Output Pictures/outputframe1.png
title: "Image Sequence Ascii Playback"
date: 2024
published: true
labels:
  - Java
summary: "Converts each image in a folder to ascii and displays each one in sequence on a JFrame to simulate video/animation"
---

<div class="text-center p-4">
  <img width="200px" src="../img/Output Pictures/outputframe2.png" class="img-thumbnail" >
  <img width="200px" src="../img/Output Pictures/outputframe3.png" class="img-thumbnail" >

</div>

Repo url: https://github.com/nathankleung/image-sequence-to-ascii

I created this project during my senior year of high school after being inspired by the course material taught in my "Computer Science A" class that involved input/output of files and my further research into JFrame from a Java textbook in the class. Through this personal project as the sole developer, I gained greater familiarity with Java's input/output Scanner class, JFrame framework, and the process of putting the ideas that I envision into code.

I had a vision for what I needed to include in my program for the goal of displaying continuous image frames as it was built off of previous knowledge of reading, writing, and displaying a single file from my classwork. I knew that as a beginner programmer, my skills would not be up to par to build an image to ascii converter myself and that I was not well versed with error handling when it came to working with multiple files. To get around these challenges, I researched for preexisting solutions to ease the work load on myself and considering that I did not need an overly personal solution for the ascii generation. This follows the process of smart questioning by making use of the resources available to me to avoid extra work and not asking repetitive questions when the answers are already available. The parts of the program that are borrowed from others can be seen from places like StackOverflow and GitHub where I recognized that these functions served to fix the problem I needed for creating the ascii and error handling while iterating through a folder.

While a very simple project, I am proud of this work since it was the first project that I really dedicated myself to on my own time outside of any class requirements and it sparked my interest in learning more about programming with Java, learning how to use a new framework with Java's JFrame, and exercised my problem solving to put all the pieces together.

Here is the function that converts each image in a folder to ascii text and displays it on a JFrame

```java
public static String createTxt(String folderName) 
{
	//Original loop creates a list of files in the folder from the directory
	//Taken from StackOverflow, modified to suit needs of this program
	//By: RoflcoptrException
    folder = new File(folderName);
	File[] listOfFiles = folder.listFiles();

	//Sorts the images in the folder. Useful for MacOS
    listOfFiles = heapSort(listOfFiles);
    if(listOfFiles != null) 
    {
    	//loops based on number of files in folder
    	for (int i = 0; i < listOfFiles.length; i=i+1) {
    		
    		if (listOfFiles[i].isFile()) 
    		{
    			fullWord = "";	//resets the text for each file
    			artName = ("frame.txt"); //Changes name of text file for each frame
    			text2ascii obj = new text2ascii(); //creates the text file
    			obj.convertToAscii(listOfFiles[i]); //creates ASCII art on text file based on the image at i position in list of files
    	    	
    	    	//prints out the ASCII art text file
    			ArrayList<String> wordsOnFile = loadFileString(artName);
    			System.out.println("");

				for(String word:wordsOnFile) 
    			{
					fullWord = fullWord + word + "\n";
    			}
				System.out.println(fullWord);
    			System.out.println("");

    			createWindow(fullWord);
				try {
					Thread.sleep(delay);
				} catch (InterruptedException e) {
					e.printStackTrace();
				}
		} 
		else if (listOfFiles[i].isDirectory()) 
		{
			System.out.println("Directory " + listOfFiles[i].getName());
		}
    	}	
    }
	return fullWord;
}
```
