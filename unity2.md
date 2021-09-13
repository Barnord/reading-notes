# Looking around in Unity

## Setup

### Objects

We only need two things here, a camera, and a player body. The player body can be anything, but I recommend you attach your camera to it.

### Components

The only component we need is the script.

## The Script

Lets start with setting our fields. We want:
- float, mouseSensitivity (mine is set to 100, adjust as desired)
- float, xRotation
- Transform, playerBody (for your player body)

Lets jump into the Start method, bear with me.
`Cursor.lockState = CursorLockMode.Locked`
I misled you, that's literally all there is to the start method.

The Update method has a little more to it, but not too much since looking around is easy once you know how the pieces fit together.

Inside Update, we want two floats, `mouseX` and `mouseY`. These floats will track how both axes of our mouse are moving by time, with our mouse sensitivity.
```
float mouseX = Input.GetAxis("Mouse X") * mouseSensitivity * Time.deltaTime;
float mouseY = Input.GetAxis("Mouse Y") * mouseSensitivity * Time.deltaTime;
```

Next we want to rotate our player body, we do thsi with a Quaternion. Don't know what that is? Me either, but they represent rotations, and that's exactly what we need right now. To set our Y axis to look with our mouse only takes one more step:
```
transform.localRotation = Quaternion.Euler(mouseY, 0f, 0f);
```

With that you should be able to look up and down, but to look side to side works differently, because we're going to actually rotate our character. Thankfully we have our playerBody stored in a field, so we can access it directly here. We want to rotate it up, because directions are a little weird in unity. So we set:
```
playerBody.Rotate(Vector3.up * mouseX);
```

And just like that we're looking around like a pro!

[How to move](unity1.md)

[<==Back](README.md)