# imagej-macro-crop
simple marcro to crop all images in the same folder with ImageJ

/////////////////////////////////////////////////////////////////////
// Ask for the input folder
inputDirectory = getDirectory("Choose a Directory");
outputDirectory = inputDirectory; // Save the cropped images in the same folder

// Get a list of all files in the input folder
list = getFileList(inputDirectory);

// Loop through all files
for (i = 0; i < list.length; i++) {
    filePath = inputDirectory + list[i];
    
// Open the image
    open(filePath);
    
// Get image dimensions
    width = getWidth();
    height = getHeight();
    
// Define the crop region
    leftCrop = 50;
    rightCrop = 50;
    newWidth = width - leftCrop - rightCrop;
    
// Perform the crop
    makeRectangle(leftCrop, 0, newWidth, height);
    run("Crop");
    
// Save the cropped image in TIFF format
    saveAs("Tiff", outputDirectory + list[i]);
    
    // Close the image
    close();
}
////////////////////////////////////////////////////////
**Instructions to Run the Script:**

1. Copy the script above.
2. Open ImageJ.
3. Go to Plugins > New > Macro.
4. Paste the script into the new macro window.
5. Run the macro by clicking on the "Run" button (the triangle icon).

**Explanation:**
The script prompts the user to choose a directory containing the images.
It then lists all files in that directory.
For each file, it opens the image, calculates the new dimensions for cropping (50 pixels removed from both left and right), performs the crop, and saves the image in the same directory with the same name but in TIFF format.
Finally, it closes the image to move on to the next one.
Feel free to modify the script if you need to change any parameters or add additional functionality. If you encounter any issues or have further questions, please let me know!
