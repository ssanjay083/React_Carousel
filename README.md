# Ex05 Image Carousel
## Date: 14-03-2026

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
## app.css
```
body {
  background-color: #e8f4ff;
  margin: 0;
  font-family: Arial, sans-serif;
}

.container {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center; 
  align-items: center;
  text-align: center;
}

.carousel-image {
  width: 400px;
  height: 230px;
  border-radius: 10px;
  box-shadow: 0px 4px 10px rgba(0,0,0,0.3);
}

.buttons button {
  margin: 10px;
  padding: 10px 20px;
  border: none;
  background-color: #3498db;
  color: white;
  border-radius: 5px;
  cursor: pointer;
}

.buttons button:hover {
  background-color: #2c80b4;
}

.dots {
  margin-top: 10px;
}

.dot {
  height: 12px;
  width: 12px;
  margin: 5px;
  background-color: gray;
  border-radius: 50%;
  display: inline-block;
}

.active {
  background-color: black;
}
```
## app.js
```
import React, { useState } from "react";
import "./App.css";

function App() {

const places = [
  {
    url: "https://images.unsplash.com/photo-1501785888041-af3ef285b470",
    name: "Beautiful Mountains"
  },
  {
    url: "https://images.unsplash.com/photo-1507525428034-b723cf961d3e",
    name: "Peaceful Beach"
  },
  {
    url: "https://images.unsplash.com/photo-1441974231531-c6227db76b6e",
    name: "Green Forest"
  }
];

  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((currentIndex + 1) % places.length);
  };

  const prevImage = () => {
    setCurrentIndex((currentIndex - 1 + places.length) % places.length);
  };

  return (
    <div className="container">

      <h2>Beautiful Places Around the World</h2>

      <img
        src={places[currentIndex].url}
        alt="place"
        className="carousel-image"
      />

      <p>{places[currentIndex].name}</p>

      <div className="buttons">
        <button onClick={prevImage}>Previous</button>
        <button onClick={nextImage}>Next</button>
      </div>

      <div className="dots">
        {places.map((_, index) => (
          <span
            key={index}
            className={index === currentIndex ? "dot active" : "dot"}
          ></span>
        ))}
      </div>

    </div>
  );
}

export default App;
```
## OUTPUT
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/6a34dae9-95e3-4088-a3bc-cd3ac11e7ea5" />
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/84a2e1da-0c4f-4385-aa24-6d2ce1100c2f" />
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/16809791-022f-45f2-9b8d-16467c950557" />





## RESULT
The program for creating Image Carousel using React is executed successfully.
