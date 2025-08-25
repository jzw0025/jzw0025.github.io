---
title: "Understanding Quaternions: A Powerful Tool for 3D Rotations"
layout: single
author: "Junchao"
date: 2023-10-01
categories:
  - Mathematics
  - Robotics
  - Computer Graphics
tags:
  - Quaternions
  - 3D Rotations
  - Euler Angles
  - Robotics
  - Aerospace
header:
  overlay_image: /assets/images/quaternions.jpg
  overlay_filter: 0.5
  caption: "Quaternions: The key to smooth and stable 3D rotations"
---

## Introduction

Quaternions are a powerful mathematical tool used to represent **3D rotations**. Unlike Euler angles, quaternions avoid issues like **gimbal lock** and provide a more stable and efficient way to handle rotations in robotics, aerospace, and computer graphics.

In this post, we'll explore the basics of quaternions, their physical meaning, and how they connect to Euler angles.

---

## Quaternion Basics

A quaternion is typically written as:
$$q = a + bi + cj + dk$$

Or in vector form:
$$q = [a, b, c, d]$$

Where:
- **`a`**: The scalar (real) part.
- **`b, c, d`**: The vector (imaginary) parts.

Together, these components encode a rotation in 3D space.

---

## Physical Meaning of Quaternion Components

Quaternions represent a rotation by an angle \( \theta \) around a unit axis \( \vec{u} = (u_x, u_y, u_z) \). The components of the quaternion are:

$$a = \cos\left(\frac{\theta}{2}\right)$$

$$b = u_x \cdot \sin\left(\frac{\theta}{2}\right)$$

$$c = u_y \cdot \sin\left(\frac{\theta}{2}\right)$$

$$d = u_z \cdot \sin\left(\frac{\theta}{2}\right)$$

### Key Points:
- **`a`** controls the rotation angle.
- **`b, c, d`** define the axis of rotation, scaled by the sine of half the angle.

This is known as the **axis-angle representation**, compactly encoded in quaternion form.

---

## Connection to Euler Angles

Euler angles describe rotation as a sequence of rotations around the X, Y, and Z axes (e.g., roll, pitch, yaw). However, they suffer from **gimbal lock**, where two axes align, causing a loss of one degree of freedom.

Quaternions avoid this by representing rotation as a single rotation around an arbitrary axis. This makes them:
- **More stable numerically**.
- **Easier to interpolate** (e.g., in animation or robotics).
- **Free from singularities**.

### Conversion Between Euler Angles and Quaternions

For a ZYX rotation order (yaw, pitch, roll), the quaternion components can be calculated as:

$$a = \cos\left(\frac{\phi}{2}\right)\cos\left(\frac{\theta}{2}\right)\cos\left(\frac{\psi}{2}\right) + \sin\left(\frac{\phi}{2}\right)\sin\left(\frac{\theta}{2}\right)\sin\left(\frac{\psi}{2}\right)$$

$$b = \sin\left(\frac{\phi}{2}\right)\cos\left(\frac{\theta}{2}\right)\cos\left(\frac{\psi}{2}\right) - \cos\left(\frac{\phi}{2}\right)\sin\left(\frac{\theta}{2}\right)\sin\left(\frac{\psi}{2}\right)$$

$$c = \cos\left(\frac{\phi}{2}\right)\sin\left(\frac{\theta}{2}\right)\cos\left(\frac{\psi}{2}\right) + \sin\left(\frac{\phi}{2}\right)\cos\left(\frac{\theta}{2}\right)\sin\left(\frac{\psi}{2}\right)$$

$$d = \cos\left(\frac{\phi}{2}\right)\cos\left(\frac{\theta}{2}\right)\sin\left(\frac{\psi}{2}\right) - \sin\left(\frac{\phi}{2}\right)\sin\left(\frac{\theta}{2}\right)\cos\left(\frac{\psi}{2}\right)$$

Where:
- \( \phi \): Roll (rotation around X-axis).
- \( \theta \): Pitch (rotation around Y-axis).
- \( \psi \): Yaw (rotation around Z-axis).

---

## Why Quaternions Matter

Quaternions are widely used in various fields due to their stability and efficiency:

### 1. **Robotics**
- Used for smooth motion planning and orientation control.
- Avoids gimbal lock, ensuring reliable operation in 3D space.

### 2. **Aerospace**
- Helps track aircraft attitude without drift.
- Essential for spacecraft orientation and control.

### 3. **Computer Graphics**
- Enables fluid camera and object rotations.
- Used in animations and game engines for smooth interpolation (e.g., SLERP - Spherical Linear Interpolation).

---

## Conclusion

Quaternions are a versatile and powerful tool for representing 3D rotations. By avoiding the pitfalls of Euler angles, they provide a stable, efficient, and intuitive way to handle rotations in robotics, aerospace, and computer graphics.