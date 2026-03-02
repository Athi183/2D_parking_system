# 🅿 2D Smart Parking Surveillance System

## 📌 Project Overview

This project is a **2D Smart Parking Surveillance Simulator** developed using **Python and Pygame**.

It simulates:

- A parking area with multiple slots
- A rotating CCTV camera
- A visual field-of-view (FOV)
- A foundation for vehicle detection and smart monitoring

The project demonstrates core **Computer Graphics concepts** such as translation, rotation, coordinate systems, and geometric transformations.

---

## 🎯 Objective

To simulate a real-world parking surveillance system using 2D graphical rendering and geometric computations.

The system visually represents:

- Parking layout
- CCTV camera scanning
- Field-of-view coverage
- (Future extension) Vehicle detection

---

## 🛠 Technologies Used

- Python 3
- Pygame Library
- Basic Geometry & Trigonometry

---

## 📂 Project Structure
2D_parking_system/
│
├── room.py → Parking area and main simulation loop
├── camera.py → Camera class with rotation and FOV
├── vehicle.py → (Planned) Vehicle logic
├── detection.py → (Planned) Detection logic
├── README.md → Project documentation


---

## 🧩 Module Explanation

---

### 1️⃣ room.py – Parking Environment

This file creates the main simulation window.

#### Responsibilities:

- Initialize Pygame
- Set window size
- Define colors
- Draw parking boundary
- Generate parking slots
- Handle main event loop
- Integrate camera module

#### Key Concepts Used:

- 2D coordinate positioning
- Rectangle drawing
- Translation using x and y coordinates
- Game loop structure

#### Parking Slot Logic:

Slots are generated automatically using:

```python
x = start_x + j * (slot_width + gap_x)
y = start_y + i * (slot_height + gap_y)

---

### 2️⃣ camera.py – Camera & Field of View System

This module simulates a rotating CCTV camera inside the parking area.

It is responsible for:

- Defining camera position
- Implementing rotation logic
- Rendering the camera body
- Drawing the Field of View (FOV)

---

#### 📌 Camera Properties

The `Camera` class contains:

- `x, y` → Position of the camera in the 2D coordinate system
- `angle` → Current direction the camera is facing (stored in degrees)

The angle changes dynamically when rotation keys are pressed.

---

#### 🔄 Camera Rotation Logic

Rotation is implemented by modifying the `angle` value:

```python
self.angle += 2
self.angle -= 2

---

#### 🔄 Camera Rotation Logic

Rotation is implemented by modifying the `angle` value:

```python
self.angle += 2
self.angle -= 2
```

- The value `2` represents **2 degrees per frame**.
- Since the game runs approximately 60 frames per second, total rotation speed depends on frame rate.
- The angle is stored in **degrees** for easier understanding.

If smoother rotation is needed, the value can be reduced:

```python
self.angle += 0.5
```

---

#### 📐 Degree to Radian Conversion

Python’s trigonometric functions (`cos`, `sin`) use radians.

Before performing calculations, the angle is converted:

```python
math.radians(self.angle)
```

This ensures accurate coordinate transformation.

---

#### 👁 Field of View (FOV) Rendering

The Field of View is represented as a triangular region.

It is calculated using trigonometric equations:

```python
x = x0 + r * cos(θ)
y = y0 + r * sin(θ)
```

Where:

- `x0, y0` → Camera position
- `r` → Viewing distance
- `θ` → Angle in radians

Two boundary angles are calculated:

- Left boundary = angle - (FOV / 2)
- Right boundary = angle + (FOV / 2)

These three points (camera position + two boundary points)
form a triangle drawn using:

```python
pygame.draw.polygon()
```

This visually represents the camera’s coverage area.

---

#### 🎨 Camera Representation

The camera is visually represented using:

```python
pygame.draw.circle()
```

To show the direction the camera is facing, a line is drawn:

```python
pygame.draw.line()
```

This direction line rotates according to the angle value,
making the rotation visually understandable.

---

#### 🧠 Concepts Demonstrated in camera.py

- 2D rotation transformation
- Trigonometric coordinate calculation
- Degree to radian conversion
- Polygon rendering
- Dynamic graphical animation
- Frame-based rotation control

---

## 🚗 3️⃣ vehicle.py – Vehicle Simulation (Planned)

This module will simulate vehicles entering the parking area.

### Responsibilities:

- Create a `Vehicle` class
- Draw vehicle as rectangle or image
- Allow movement using keyboard
- Track vehicle position
- Detect parking slot entry (optional)

### Planned Features:

- Vehicle movement using WASD or arrow keys
- Parking slot collision detection
- Position tracking in coordinate space

### Concepts Covered:

- Translation (x and y movement)
- Collision detection
- Object interaction
- Real-time position updates

---

## 🎥 4️⃣ detection.py – Smart Detection Logic (Planned)

This module will connect the camera and vehicle.

### Responsibilities:

- Check if vehicle lies inside camera FOV
- Stop camera rotation upon detection
- Display alert message
- Resume rotation on reset command

### Detection Logic (Mathematical Approach):

1. Calculate distance between camera and vehicle.
2. Calculate angle between camera direction and vehicle position.
3. Check if:
   - Distance ≤ FOV distance
   - Angle difference ≤ (FOV / 2)

If both conditions are satisfied → Vehicle detected.

### Concepts Covered:

- Distance formula:
  ```
  √((x2 - x1)² + (y2 - y1)²)
  ```
- Angle calculation using trigonometry
- Conditional geometric checking
- Logical control of animation flow

---

## 🔄 System Workflow

1. Room is created.
2. Parking slots are generated automatically.
3. Camera rotates continuously.
4. Vehicle enters parking area.
5. Detection system checks if vehicle is inside FOV.
6. If detected:
   - Camera stops rotating
   - Alert message is displayed
7. When reset key is pressed:
   - Camera resumes scanning

---

## 🎓 Computer Graphics Concepts Demonstrated

- 2D coordinate system
- Translation
- Rotation transformation
- Trigonometric coordinate conversion
- Polygon rendering
- Interactive simulation
- Frame-based animation
- Modular programming design

---

## 🌍 Real-World Relevance

This project simulates a **PTZ (Pan-Tilt-Zoom) surveillance camera system** used in real-world parking areas.

It demonstrates how camera coverage is limited by:

- Viewing angle
- Distance
- Direction

It mimics intelligent surveillance systems that monitor parking areas and detect vehicles within coverage zones.

---

## 🚀 How To Run The Project

1. Activate virtual environment:

```bash
source venv/bin/activate
```

2. Run main simulation file:

```bash
python room.py
```

3. Use arrow keys to rotate the camera.

---

## 🧠 Learning Outcomes

From this project, we learned:

- How graphical systems use coordinate geometry
- How rotation is implemented using trigonometry
- How real-world surveillance systems can be simulated mathematically
- How modular programming improves clarity and scalability
- How animation works using frame-based updates

---

## 📈 Future Enhancements

- Add realistic vehicle sprites
- Implement smart detection logic
- Add parking slot occupancy tracking
- Add multiple cameras
- Add alert dashboard
- Add automatic PTZ scanning pattern

---

## 👥 Team Workflow

| Member | Responsibility |
|--------|---------------|
| Member 1 | Parking layout & window system |
| Member 2 | Camera rotation & FOV |
| Member 3 | Vehicle movement |
| Member 4 | Detection & smart control |

---

## 📌 Final Summary

This project is a structured 2D simulation of a smart parking surveillance system using Python and Pygame.  
It demonstrates core computer graphics principles including translation, rotation, and geometric transformations within an interactive environment.

The system serves as a foundational model for intelligent surveillance simulation in 2D space.
