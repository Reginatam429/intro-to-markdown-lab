# Regina's Collision Detection Tutorial for Dummies
 
What is **collision detection**? 

When you play a game and an object like a laser shot interacts with the target or if you want to simulate snowflakes colliding into one another as they fall how does your program know they touched? thats made possible with collision detection. Its finding the points of contact between 2D and 3D objects.
![squares colliding](https://chriscourses.com/blog/collision-detection.jpg)

---
## Types of Collision Detection

### 1. Bounding Box Collision (AABB - Axis-Aligned Bounding Box)
This is the easiest and most common method that uses rectangles around object to check if theres overlap. Its great for square shaped objects.

### 2. Circle Collision
Circle collision uses circles around the objects to check if their radii overlap. Good for rouded objects like planets or balls.

### 3. Pixel-Perfect Collision
This checks if the actual pixels overlap, much more complex and computationally expensive.

## The Choice I made for my Space Cat Shooter Game
![AABB example](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSVoVbHz79d5kEAHun4OspECpn33uDSfji-kg&s)

I chose to use **Bounding Box Collision Detection (AABB)** for my game since most of my objects used png which tend to be retanglar shaped and for simplicity as my first project attempting this. 

The idea is that each object has an `x`,`y`, `width`, and `height` attribute. If one rectangle object overlaps another one, you have a collision. 

Heres some sample code of what a collision function looks like:
```javascript
function collisionCheck(obj1, obj2) {
    return (
        obj1.x < obj2.x + obj2.width &&
        obj1.x + obj1.width > obj2.x &&
        obj1.y < obj2.y + obj2.height &&
        obj1.y + obj1.height > obj2.y
    );
}

    // Example of how function is used:

// objects are expected to have x, y, width, and height properties
let player = { x: 50, y: 50, width: 40, height: 40 };
let enemy = { x: 70, y: 70, width: 40, height: 40 };

if (collisionCheck(player, enemy)) {
    console.log("Collision detected!");
}
```

### Breaking Down the `collisionCheck` function:
1. `obj1.x < obj2.x + obj2.width`
    - This is checking if the **left side** of `obj1` is to the left of the **right side** of `obj2`

2. `obj1.x + obj1.width > obj2.x`

    - Checks if the right side of obj1 is to the right of the left side of obj2. This means obj1 is not completely to the left of obj2.

3. `obj1.y < obj2.y + obj2.height`
    - Checks if the top of obj1 is above the bottom of obj2.
    obj1 is not completely below obj2.

4. `obj1.y + obj1.height > obj2.y`
    - Checks if the bottom of obj1 is below the top of obj2.
    obj1 is not completely above obj2.

** How it works: **
- For two rectangles to be colliding, their `x` and `y` ranges have to be overlapping
- If any of the four conditions are false, there is no collision
- If all four conditions are true, you have a collision

![Nyan cat](https://media3.giphy.com/media/bjE9JbNSckM0w/200w.gif?cid=6c09b952l7k5r3md8lrvatxxcj824dcavtmta7pnykm9jka4&ep=v1_stickers_search&rid=200w.gif&ct=s)

### Hope this helps you make your games or graphics too!


## Resources for further reading:
- [MDN Guide to 2D Collision Detection](https://developer.mozilla.org/en-US/docs/Games/Techniques/2D_collision_detection)
- [MDN GameDev Canvas tutorial for Collision Detection](https://developer.mozilla.org/en-US/docs/Games/Techniques/2D_collision_detection)