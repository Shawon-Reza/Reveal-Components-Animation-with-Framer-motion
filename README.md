# 🎬 Scroll Reveal Animations with Framer Motion

## 📌 Introduction

Have you ever noticed how modern websites make content smoothly appear as you scroll?

Instead of displaying everything at once, sections gradually fade, slide, or scale into view when they enter the viewport. This technique is known as **Scroll Reveal Animation**.

One of the easiest ways to implement this effect in React and Next.js applications is by using **Framer Motion**.

---

## 🧠 What is Scroll Reveal Animation?

Scroll Reveal Animation is a UI technique that triggers animations when elements become visible on the screen.

Rather than rendering content instantly, elements can:

* Fade in
* Slide up
* Slide down
* Slide from left or right
* Zoom into view

This creates a more engaging and modern user experience.

---

## ⚙️ How It Works

The basic workflow looks like this:

```txt
Page Loads
     ↓
Component Starts Hidden
     ↓
User Scrolls
     ↓
Component Enters Viewport
     ↓
Animation Triggers
     ↓
Element Becomes Visible
```

---

## 📦 Installation

```bash
npm install framer-motion
```

---

## 🧩 Basic Example

```tsx
<motion.div
  initial={{ opacity: 0, y: 100 }}
  whileInView={{ opacity: 1, y: 0 }}
  viewport={{
    once: false,
    amount: 0.2,
  }}
  transition={{
    duration: 0.8,
    ease: "easeOut",
  }}
>
  Content
</motion.div>
```

---

# Process (Next.Js)
## Step 1 (Install Frqamer motion)
npm install motion

## Step 2 (Create a Component )
```jsx
    "use client";

import { motion } from "framer-motion";
import { ReactNode } from "react";

interface RevealProps {
  children: ReactNode;
}

export default function RevealAnimation({ children }: RevealProps) {
  return (
    <motion.div
      initial={{ opacity: 0, y: 80 }}
      whileInView={{ opacity: 1, y: 0 }}
      viewport={{
        once: false,
        amount: 0.2,
      }}
      transition={{
        duration: 1.9,
        ease: "easeOut",
      }}
    >
      {children}
    </motion.div>
  );
}
```
## Step 3 ( Now you can use the this as a parent component)
```jsx

      <RevealAnimation>
        <section
          id="about"
        >
          <AboutMe />
        </section>
      </RevealAnimation>
```

## 🔍 Understanding the Properties

### initial

Defines the starting state before the animation begins.

```tsx
initial={{ opacity: 0, y: 100 }}
```

Meaning:

* opacity: 0 → invisible
* y: 100 → positioned 100px lower

---

### whileInView

Defines the animation target state when the component enters the viewport.

```tsx
whileInView={{ opacity: 1, y: 0 }}
```

Meaning:

* opacity: 1 → fully visible
* y: 0 → original position

---

### viewport

Controls when the animation should trigger.

```tsx
viewport={{
  once: false,
  amount: 0.2,
}}
```

#### once

```tsx
once: true
```

Animation runs only once.

```tsx
once: false
```

Animation runs every time the element enters the viewport.

---

#### amount

```tsx
amount: 0.2
```

Animation starts when 20% of the element is visible.

Examples:

```tsx
amount: 0
```

Trigger immediately.

```tsx
amount: 0.5
```

Trigger when 50% is visible.

```tsx
amount: 1
```

Trigger when fully visible.

---

### transition

Controls animation timing and behavior.

```tsx
transition={{
  duration: 0.8,
  ease: "easeOut",
}}
```

#### duration

Controls how long the animation lasts.

```tsx
duration: 0.3
```

Fast

```tsx
duration: 0.8
```

Smooth

```tsx
duration: 2
```

Slow

---

#### ease

Controls animation speed curves.

```tsx
ease: "linear"
```

Constant speed

```tsx
ease: "easeIn"
```

Slow → Fast

```tsx
ease: "easeOut"
```

Fast → Slow

```tsx
ease: "easeInOut"
```

Slow → Fast → Slow

---

## 🎨 Common Reveal Effects 

### Fade In

```tsx
initial={{ opacity: 0 }}
whileInView={{ opacity: 1 }}
```

---

### Fade Up

```tsx
initial={{ opacity: 0, y: 50 }}
whileInView={{ opacity: 1, y: 0 }}
```

---

### Fade Down

```tsx
initial={{ opacity: 0, y: -50 }}
whileInView={{ opacity: 1, y: 0 }}
```

---

### Fade Left

```tsx
initial={{ opacity: 0, x: -50 }}
whileInView={{ opacity: 1, x: 0 }}
```

---

### Fade Right

```tsx
initial={{ opacity: 0, x: 50 }}
whileInView={{ opacity: 1, x: 0 }}
```

---

### Zoom In

```tsx
initial={{ opacity: 0, scale: 0.8 }}
whileInView={{ opacity: 1, scale: 1 }}
```

---

### Zoom Out

```tsx
initial={{ opacity: 0, scale: 1.2 }}
whileInView={{ opacity: 1, scale: 1 }}
```

---

### Pop Up

```tsx
initial={{ opacity: 0, scale: 0.5 }}
whileInView={{ opacity: 1, scale: 1 }}
```

---

### Rotate Left

```tsx
initial={{ opacity: 0, rotate: -15 }}
whileInView={{ opacity: 1, rotate: 0 }}
```

---

### Rotate Right

```tsx
initial={{ opacity: 0, rotate: 15 }}
whileInView={{ opacity: 1, rotate: 0 }}
```

---

### Rotate + Zoom

```tsx
initial={{
  opacity: 0,
  rotate: 20,
  scale: 0.8,
}}
whileInView={{
  opacity: 1,
  rotate: 0,
  scale: 1,
}}
```

---

### Blur Reveal

```tsx
initial={{
  opacity: 0,
  filter: "blur(10px)",
}}
whileInView={{
  opacity: 1,
  filter: "blur(0px)",
}}
```

---

### Blur Up

```tsx
initial={{
  opacity: 0,
  y: 30,
  filter: "blur(8px)",
}}
whileInView={{
  opacity: 1,
  y: 0,
  filter: "blur(0px)",
}}
```

---

### Fade + Zoom

```tsx
initial={{
  opacity: 0,
  scale: 0.8,
}}
whileInView={{
  opacity: 1,
  scale: 1,
}}
```

---

### Fade + Slide + Zoom

```tsx
initial={{
  opacity: 0,
  y: 50,
  scale: 0.9,
}}
whileInView={{
  opacity: 1,
  y: 0,
  scale: 1,
}}
```

---

### Fade + Rotate + Zoom

```tsx
initial={{
  opacity: 0,
  scale: 0.8,
  rotate: 10,
}}
whileInView={{
  opacity: 1,
  scale: 1,
  rotate: 0,
}}
```

---

### Lift Up Card

```tsx
initial={{
  opacity: 0,
  y: 80,
}}
whileInView={{
  opacity: 1,
  y: 0,
}}
```

---

### Floating Card

```tsx
initial={{
  opacity: 0,
  y: 50,
  scale: 0.95,
}}
whileInView={{
  opacity: 1,
  y: 0,
  scale: 1,
}}
```

---

### Text Reveal

```tsx
initial={{
  opacity: 0,
  y: 20,
}}
whileInView={{
  opacity: 1,
  y: 0,
}}
```

---

### Headline Reveal

```tsx
initial={{
  opacity: 0,
  y: 100,
}}
whileInView={{
  opacity: 1,
  y: 0,
}}
```

---

### Image Zoom Reveal

```tsx
initial={{
  opacity: 0,
  scale: 1.2,
}}
whileInView={{
  opacity: 1,
  scale: 1,
}}
```

---

### Image Slide Reveal

```tsx
initial={{
  opacity: 0,
  x: 100,
}}
whileInView={{
  opacity: 1,
  x: 0,
}}
```

---

### Premium Reveal (Recommended)

```tsx
initial={{
  opacity: 0,
  y: 40,
  filter: "blur(10px)",
}}
whileInView={{
  opacity: 1,
  y: 0,
  filter: "blur(0px)",
}}
```

---

### Premium Hero Reveal

```tsx
initial={{
  opacity: 0,
  y: 100,
  scale: 0.95,
}}
whileInView={{
  opacity: 1,
  y: 0,
  scale: 1,
}}
```

---

### Modern Glassmorphism Reveal

```tsx
initial={{
  opacity: 0,
  y: 50,
  filter: "blur(20px)",
  scale: 0.95,
}}
whileInView={{
  opacity: 1,
  y: 0,
  filter: "blur(0px)",
  scale: 1,
}}
```





