# Ex06 BMI Calculator
## Date: 16/05/2025

## AIM
To create a BMI calculator using React Router 

## ALGORITHM
### STEP 1 State Initialization
Manage the current page (Home or Calculator) using React Router.

### STEP 2 User Input
Accept weight and height inputs from the user.

### STEP 3 BMI Calculation
Calculate the BMI based on user input.

### STEP 4 Categorization
Classify the BMI result into categories (Underweight, Normal weight, Overweight, Obesity).

### STEP 5 Navigation
Navigate between pages using React Router.

## PROGRAM

### App.js
```
import React, { useState } from 'react';   
import { BrowserRouter as Router, Route, Link, Routes } from 'react-router-dom';  
import './App.css';

function Home() {
  return (
    <div className="home">
      <h1>Welcome to the BMI Calculator</h1>
      <Link to="/calculator">
        <button>Go to Calculator</button>
      </Link>
    </div>
  );
}

function Calculator() {
  const [weight, setWeight] = useState('');
  const [height, setHeight] = useState('');
  const [bmi, setBmi] = useState(null);
  const [category, setCategory] = useState('');

  const handleSubmit = (e) => {
    e.preventDefault();

     const weightValue = parseFloat(weight);
    const heightValue = parseFloat(height);

     if (isNaN(weightValue) || isNaN(heightValue) || heightValue <= 0) {
      alert('Please enter valid weight and height');
      return;
    }

     const bmiValue = (weightValue / (heightValue * heightValue)).toFixed(2);
    setBmi(bmiValue);

     if (bmiValue < 18.5) {
      setCategory('Underweight');
    } else if (bmiValue >= 18.5 && bmiValue < 24.9) {
      setCategory('Normal weight');
    } else if (bmiValue >= 25 && bmiValue < 29.9) {
      setCategory('Overweight');
    } else {
      setCategory('Obesity');
    }
  };

  return (
    <div className="calculator">
      <h2>BMI Calculator</h2>
      <form onSubmit={handleSubmit}>
        <label>
          Weight (kg):
          <input
            type="number"
            value={weight}
            onChange={(e) => setWeight(e.target.value)}
            required
            step="0.1"  
          />
        </label>
        <br />
        <label>
          Height (m):
          <input
            type="number"
            value={height}
            onChange={(e) => setHeight(e.target.value)}
            required
            step="0.01" 
          />
        </label>
        <br />
        <button type="submit">Calculate BMI</button>
      </form>
      {bmi && (
        <div>
          <h3>Your BMI: {bmi}</h3>
          <p>Category: {category}</p>
        </div>
      )}
      <Link to="/">Go to Home</Link>
    </div>
  );
}

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/calculator" element={<Calculator />} />
      </Routes>
    </Router>
  );
}

export default App;
```

### App.css
```
 * {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Arial', sans-serif;
  background: linear-gradient(135deg, #5f2c82, #49a09d);
  color: #fff;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.home {
  text-align: center;
  background-color: rgba(0, 0, 0, 0.6);  
  padding: 50px;
  border-radius: 15px;
  width: 70%;
  max-width: 400px;
}

.home h1 {
  font-size: 2.5rem;
  margin-bottom: 20px;
}

.home button {
  padding: 12px 25px;
  font-size: 1.2rem;
  background-color: #ff5722;
  border: none;
  border-radius: 30px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.home button:hover {
  background-color: #ff784e;
  transform: scale(1.1);
}

.home a {
  margin-top: 20px;
  display: inline-block;
  font-size: 1.1rem;
  text-decoration: none;
  color: #ff5722;
  transition: color 0.3s ease;
}

.home a:hover {
  color: #ff784e;
}

 .calculator {
  text-align: center;
  background-color: rgba(0, 0, 0, 0.6); 
  padding: 50px;
  border-radius: 15px;
  width: 70%;
  max-width: 500px;
  margin-top: 30px;
}

.calculator h2 {
  font-size: 2.2rem;
  margin-bottom: 20px;
  color: #ffeb3b;
}

.calculator form {
  margin-bottom: 20px;
}

.calculator label {
  font-size: 1.2rem;
  margin-right: 10px;
}

.calculator input {
  padding: 10px;
  font-size: 1rem;
  margin: 15px 0;
  border-radius: 5px;
  border: 2px solid #ddd;
  width: 80%;
  max-width: 300px;
  text-align: center;
  background-color: #fff;
}

.calculator button {
  padding: 12px 25px;
  font-size: 1.2rem;
  background-color: #4CAF50;
  border: none;
  border-radius: 30px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.calculator button:hover {
  background-color: #45a049;
  transform: scale(1.05);
}

.calculator h3 {
  font-size: 1.5rem;
  margin-top: 20px;
  color: #ffeb3b;
}

.calculator p {
  font-size: 1.2rem;
  margin-top: 10px;
  color: #f0f0f0;
}

.calculator a {
  margin-top: 20px;
  display: block;
  font-size: 1.2rem;
  text-decoration: none;
  color: #4CAF50;
  transition: color 0.3s ease;
}

.calculator a:hover {
  color: #45a049;
}

 @media screen and (max-width: 768px) {
  .home, .calculator {
    width: 90%;
    padding: 30px;
  }

  .home h1 {
    font-size: 2rem;
  }

  .calculator h2 {
    font-size: 1.8rem;
  }

  .calculator label, .calculator input {
    font-size: 1rem;
  }
}
```


## OUTPUT

![Screenshot (28)](https://github.com/user-attachments/assets/46bfb905-bf9a-49c9-a694-c550be89ad7f)
![Screenshot (29)](https://github.com/user-attachments/assets/8948e305-19ac-455e-b905-9dd861bb441b)



## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
