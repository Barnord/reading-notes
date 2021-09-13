# Moving with the Character Controller in Unity

## Setup

You will need:
- player object
- camera
- empty object

Drag the camera and the empty object (this will be the ground check) into your player object.

## Components

Our only components here are on the player object, they are:
- Character Controller
- Rigidbody
- Script

We don't need to do anything with the character controller yet, but we do need to lock all the rotations on the Rigidbody. Weird, I know, but trust me.

That leaves us...

## The Script

NOTE - Some of these aren't necessary until we try to use the grappling hook, added in the next installment.

Lets start with our public fields, we are going to want:
- CharacterController
- Camera
- Transform
- LayerMask
- bool
- float, speed (adjust as desired, mine is 12)
- float, gravity (adjust as desired, mine is 8.91)
- float, groundDistance (adjust as desired, mine is .4) This is for calculating if we're grounded.
- float, jumpHeight (adjust as desired, mine is 3)
- Vector3, velocity

None of these actually have to be public, however I find it easier to change them for experimenting when they are.

Once we have all those instantiated, it's a good idea to save and configure your CharacterController, Camera, Transform, and LayerMask in Unity.

Drag your character controller component into your CharacterController field, Camera into Camera field, our empty object into the Transform field (note, the empty object should be positioned at the bottom of your character model), and set your LayerMask to your ground layer, assuming you've made one already.

Next we'll make a `HandleMovement` method, two of the three variables we want in here are two floats, `x` and `z`. We'll set x to `Input.GetAxis("Horizontal")` and z to `Input.GetAxis("Vertical")`. These are both set in your preferences in unity. The default buttons are WASD.

The last variable is going to be a Vector3, we'll call it `move`. We want `move` to be a Vector3 that represents what buttons we're pushing to move, so we'll set `Vector3 move = transform.right * x + transform.forward * z;`. Lastly we'll set `controller.move(move * speed * Time.deltaTime)`. Now in Unity, we should be able to move our character around.

Last step, jumping! We want an if statement, checking if we're grounded, and if our jump button has been pressed. the two things we want to check are `Input.GetKeyDown(KeyCode.Space)` (replace space with you desired jump button) and the bool we set a public field for. If both of these things are true, we want to jump, that looks like `velocity.y = Mathf.Sqrt(jumpHeight * -2 * gravity);`

This would be great, if we ever changed our isGrounded status. Lets write something up to do that for us. Mine looks like this:
```
isGrounded = Physics.CheckSphere(groundCheck.position, groundDistance, groundMask);

        if (isGrounded && velocity.y < 0)
        {
            velocity.y = -2f;
        }
```

With that, you should be running and jumping like a pro that can't look around because that's a different script.

[How to look around](unity2.md)

[<==Back](README.md)