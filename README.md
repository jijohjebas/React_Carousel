# Ex05 Image Carousel
## Date:

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
App.jsx
```
import React, { useState, useEffect } from "react";
import "./App.css";

const App = () => {
  const images = [
    { src: "https://images.unsplash.com/photo-1503919483171-9ffc1debc390?ixlib=rb-4.1.0&auto=format&fit=crop&q=80&w=1170", name: "Spring" },
    { src: "https://images.unsplash.com/photo-1586902197503-e71026292412?ixlib=rb-4.1.0&auto=format&fit=crop&q=80&w=1172", name: "Summer" },
    { src: "https://images.unsplash.com/photo-1501973801540-537f08ccae7b?ixlib=rb-4.1.0&auto=format&fit=crop&q=80&w=1172", name: "Autumn" },
    { src: "https://images.unsplash.com/photo-1453306458620-5bbef13a5bca?ixlib=rb-4.1.0&auto=format&fit=crop&q=80&w=1170", name: "Winter" },
    { src: "https://images.unsplash.com/photo-1619260584294-8a4e63f5ade5?ixlib=rb-4.1.0&auto=format&fit=crop&q=80&w=1170", name: "Monsoon" },
  ];

  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => setCurrentIndex((prev) => (prev + 1) % images.length);
  const prevImage = () => setCurrentIndex((prev) => (prev - 1 + images.length) % images.length);

  // Automatically change image every 3 seconds
  useEffect(() => {
    const interval = setInterval(nextImage, 3000);
    return () => clearInterval(interval); // Cleanup on unmount
  }, []);

  return (
    <div className="app-background">
      <h1 className="heading">Image Carousel</h1>
      <p className="tagline">Seasons Around the Year</p>

      <div className="carousel-container">
        <img
          src={images[currentIndex].src}
          alt={images[currentIndex].name}
          className="carousel-image"
        />
        <h3 className="image-name">{images[currentIndex].name}</h3>
        <div className="button-group">
          <button onClick={prevImage}>Previous</button>
          <button onClick={nextImage}>Next</button>
        </div>
      </div>
    </div>
  );
};

export default App;
```
App.css
```

.app-background {
  min-height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: linear-gradient(135deg, #da90c1a2);
  font-family: 'Poppins', sans-serif;
  margin: 0;
  overflow: hidden;
  
}

.heading {
  color:black;
  text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.4);
  font-size: 2.5rem;
  margin-bottom: 5px;
  text-align: center;
  font-family: Georgia, 'Times New Roman', Times, serif;
}


.tagline {
  margin-top: 0;
  margin-bottom: 25px;
  font-size: 22px;
  color: #fff8e1;
  text-align: center;
  font-weight: 600;
  letter-spacing: 1px;
  text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.3);
}

.carousel-container {
  text-align: center;
  background: white;
  padding: 25px;
  border-radius: 20px;
  box-shadow: 0 6px 25px rgba(0, 0, 0, 0.3);
  width: 650px;
  transition: transform 0.3s ease;
}

.carousel-container:hover {
  transform: scale(1.02);
}

.carousel-image {
  width: 600px;
  height: 300px;
  border-radius: 15px;
  object-fit: cover;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
}

.image-name {
  margin-top: 12px;
  font-size: 20px;
  font-weight: 600;
  color: #333;
}

.button-group {
  margin-top: 15px;
}

button {
  background-color: #4a90e2;
  color: white;
  border: none;
  padding: 10px 18px;
  border-radius: 8px;
  cursor: pointer;
  margin: 0 10px;
  font-size: 15px;
  transition: all 0.3s ease;
}

button:hover {
  background-color: #357abd;
  transform: scale(1.05);
}
.footer {
  position: fixed;
  bottom: 10px;
  left: 0;
  width: 100%;
  text-align: center;
  color:black;
  font-weight: 500;
  font-size: 1.1rem;
}
```


## OUTPUT
<img width="1911" height="951" alt="image" src="https://github.com/user-attachments/assets/9576e706-fa11-4964-b6e1-68016e71fcb2" />
<img width="1905" height="944" alt="image" src="https://github.com/user-attachments/assets/ea09f687-bc96-4b37-9749-5928a88397c1" />
<img width="1905" height="933" alt="image" src="https://github.com/user-attachments/assets/a42c6a84-4068-44d1-974b-89a861ab82b1" />


## RESULT
The program for creating Image Carousel using React is executed successfully.
