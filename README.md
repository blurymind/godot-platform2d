# godot-platform2d
This addon provides 2 new node types for 2d platformer-style games (both inherit from StaticBody2D):
- ThinPlatform: this object is defined by a curve and provides a StaticBody2d that "follows" that curve. It is drawn using a texture that is rendered along that curve. It can be used to create thin platforms.
- ThickPlatform: this object is defined by a closed curve and provides a StaticBody2d inside that curve. It is drawn using a "fill" texture and "border" textures. There are 2 border textures that are used depending on the edge angle.

## Common exported variables

- **MovingPlatform** is a boolean parameter that will automatically update the platform's constant linear velocity when the platform is moving.
- **Curve** is the curve that defines the platform's shape (make sure to make it unique when copying a platform or the curve will be shared)
- **Bake Interval** is the distance between 2 points in the rendered platform. Keep this as high as possible (depending on the platform's shape) to improve rendering performance

## ThinPlatform exported variables

- **Left Texture** is the texture drawn on the left side of the platform.
- **Mid Texture** is the texture used to draw the platform. It must have the *repeat* attribute.
- **Right Texture** is the texture drawn on the right side of the platform.
- ** Left Overflow** (resp. ** Right Overflow**) is the "amount" of the left (resp. right) texture that "overflows" from the platform (useful when the texture shows non-solid stuff like grass).
- **Thickness** is the thickness of the platform.
- **Position** is the position of the curve in the platform's thickness and can be used to adjust the positions of the texture and the StaticBody2D. Set it to 1 when the texture has no perspective effect (the world is strictly viewed from the side) and somewhere between 0 and 1 when the top of platforms is drawn.

## ThickPlatform exported variables

- **Fill Texture** is the texture used to fill the platform. It must have the *repeat* attribute.
- **Top Texture** is a texture used to draw the edge on the top of the of the platform. It must have the *repeat* attribute.
- **Top Left/Right Texture** are the textures drawn on the edges of the top texture.
- **Side Texture** is a texture used to draw the edge of sides and bottom of the platform. It must have the *repeat* attribute.
- **Top/Side Thickness** are the thickness of the border textures
- **Top/Side Position** are the position of the curve in the platform's border and can be used to adjust the positions of the textures and the StaticBody2D.
- **Top Left/Right Overflow** is the "amount" of the edge texture that "overflows" from the top.
- **Angle** is the threshold angle used to select between top and side textures. Transitions between textures only happen at control points.

## Materials

ThinPlatform and ThickPlatform exported variables (except the common ones) define how the platforms look. They can be applied using the **<Materials>** OptionButton in the 2D view's toolbar and named (and added to the list) using the text entry. I know it is counter-intuitive and will rework it later. :p
