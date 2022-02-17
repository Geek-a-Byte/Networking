## Trilateration

<img src="https://user-images.githubusercontent.com/59027621/154419924-244f70b7-0726-4bd5-b027-489006ae414e.png" width="200px" height="150px"><img src="https://user-images.githubusercontent.com/59027621/154420037-42b7059f-3527-4523-9da1-85f55534c83d.png" width="200px" height="150px"><img src="https://user-images.githubusercontent.com/59027621/154420039-e3d86b1f-2637-4347-965d-aaeb95638f63.png" width="200px" height="150px"><img src="https://user-images.githubusercontent.com/59027621/154420044-8073e7b3-6435-44d3-b67f-55dd45b4ca76.png" width="200px" height="150px">

- Trilateration involves measuring distances.
- Trilateration Measures Distance, Not Angles

## How does the GPS system pinpoint your location using trilateration?
- Using a simple two-dimensional example, let’s imagine we have three GPS satellites each with a known position in space.
- Really, all that satellites do is broadcast a signal for your GPS receiver to pick up with a specific time and distance.
- For example, the first satellite broadcasts a signal that eventually hits your GPS receiver. We don’t know the angle, but we do know the distance. That’s why this distance forms a circle equal in all directions.
- This means that your GPS position could be anywhere on this circle at this specific radius.

## What happens when your GPS receives a second signal?
- Again, this distance is equally broadcasted in all directions until it hits your GPS receiver. This means that the distance could be anywhere on that circle.
But this time, we have two known distances from two satellites. With two signals, the precise position could be any of the two points where the circles intersect.
- Because we have a third satellite, it reveals your true location where all three circles intersect.
Using three distances, trilateration can pinpoint a precise location. Each satellite is at the center of a sphere and where they all intersect is the position of the GPS receiver.
- As the position of the GPS receiver moves, the radius of each circle (distance) will also change.
- But the reality is in our three-dimensional world that GPS satellites broadcast signals as a sphere.
- Each satellite is at the center of a sphere.
- Where all spheres intersect determines the position of the GPS receiver.
