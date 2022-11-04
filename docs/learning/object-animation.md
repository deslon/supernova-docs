It`s possible to animate any object. This page explains how to make the animation work in many ways and ease functions. Animations in Supernova are made by Actions. These Actions can be used in almost all Scene objects.

There are these types of actions:

* TimedAction
    * PositionAction
    * RotationAction
    * ScaleAction
    * ColorAction
    * AlphaAction
* ParticlesAnimation
* SpriteAnimation
* Animation

### Action control

Any kind of **action** can be controlled with these tree main methods:

| Method | Description |
| ----- | ----------- |
| ```start()``` | Start an Action ou resume if is paused. |
| ```stop()``` | Stop and reset it timestamp. |
| ```pause()``` | Pause an Action, could be resumed with run(). |

### Action events

Also, you can use actions with these callback events:

| Event | Description |
| ----- | ----------- |
| ```onStart()``` | When method Start() is called. |
| ```onPause()``` | When method pause() is called. |
| ```onStop()``` | When method stop() is called. |

## TimedAction

TimedAction is a generic type of action that has the values ```time``` and ```value```. Both values can range from 0 to 1. The ```time``` is always fixed by a pre-defined duration, but ```value``` is calculated by an ease function. ```Value``` can be controlled by both pre-defined functions and user-defined functions.

Getting value and time from Action:

=== ":octicons-file-code-16: `C++`"

    ``` c++
    float time = action.getTime();
    float value = action.getValue();
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    time = action:getTime()
    value = action:getValue()
    ```

| Used components:                     |
| ------------------------------------ |
| ActionComponent                      |
| TimedActionComponent                 |

Example how to use **TimedAction** class that is activating on touch start and on every step triangle is moved:

=== ":octicons-file-code-16: `C++`"

    ``` c++
    #include "Supernova.h"

    #include "Scene.h"
    #include "Polygon.h"
    #include "Camera.h"
    #include "TimeAction.h"
    #include "MoveAction.h"

    using namespace Supernova;

    Polygon triangle;
    Scene scene;
    TimeAction* action;

    void onActionOnStep(Object* object);
    void onTouchStart(float x, float y);

    void init(){
        Engine::setCanvasSize(1000, 480);

        triangle.addVertex(Vector3(0, -100, 0));
        triangle.addVertex(Vector3(-50, 50, 0));
        triangle.addVertex(Vector3(50, 50, 0));

        triangle.setPosition(Vector3(300, 300, 0));
        triangle.setColor(0.6, 0.2, 0.6, 1);

        scene.addObject(&triangle);

        action = new TimeAction(2, true);

        action->setFunctionType(S_LINEAR);
        triangle.addAction(action);

        action->onStep = onActionOnStep;

        Engine::setScene(&scene);
        Engine::onTouchPress = onTouchPress;
    }

    void onActionOnStep(Object* object){
        object->setPosition(200 + action->getValue() * 100, 200);
    }

    void onTouchStart(float x, float y){
        if (action->isRunning())
            action->pause();
        else
            action->run();
    }
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    Engine.setCanvasSize(1000,480)

    scene = Scene()
    triangle = Polygon()

    triangle:addVertex(0, -100, 0)
    triangle:addVertex(-50, 50, 0)
    triangle:addVertex(50, 50, 0)

    triangle:setPosition(300,300,0)
    triangle:setColor(0.6, 0.2, 0.6, 1)

    scene:addObject(triangle)

    action = TimeAction(2, false)

    action:setFunctionType(TimeAction.LINEAR)
    triangle:addAction(action)

    Engine.setScene(scene)

    function onActionOnStep(object)
        object:setPosition2D(200 + action:getValue() * 100, 200);
    end
    action.onStep = onActionOnStep

    function onTouchStart(x, y)
        if (action:isRunning()) then
            action:pause()
        else
            action:run()
        end
    end
    Engine.onTouchPress = onTouchPress
    ```

Similar to the previous example, the same function can be used with **MoveAction** instead of **TimeAction**. This time it is no longer necessary to use ```onStep()```:

=== ":octicons-file-code-16: `C++`"

    ``` c++
    #include "Supernova.h"

    #include "Scene.h"
    #include "Polygon.h"
    #include "Camera.h"
    #include "MoveAction.h"

    using namespace Supernova;

    Polygon triangle;
    Scene scene;
    MoveAction* action;

    void onTouchStart(float x, float y);

    void init(){
        Engine::setCanvasSize(1000, 480);

        triangle.addVertex(Vector3(0, -100, 0));
        triangle.addVertex(Vector3(-50, 50, 0));
        triangle.addVertex(Vector3(50, 50, 0));

        triangle.setPosition(Vector3(300, 300, 0));
        triangle.setColor(0.6, 0.2, 0.6, 1);

        scene.addObject(&triangle);

        action = new MoveAction(triangle.getPosition(), Vector3(0,10,0), 2, true);

        action->setFunctionType(S_LINEAR);
        triangle.addAction(action);
        action->run();

        Engine::setScene(&scene);
        Engine::onTouchPress = onTouchPress;
    }

    void onTouchStart(float x, float y){
        if (action->isRunning())
            action->pause();
        else
            action->run();
    }
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    Engine.setCanvasSize(1000,480)

    scene = Scene()
    triangle = Polygon()

    triangle:addVertex(0, -100, 0)
    triangle:addVertex(-50, 50, 0)
    triangle:addVertex(50, 50, 0)

    triangle:setPosition(300,300,0)
    triangle:setColor(0.6, 0.2, 0.6, 1)

    scene:addObject(triangle)

    action = MoveAction(triangle.position, Vector3(500,700,0), 2, true)

    action:setFunctionType(Action.EASE_ELASTIC_IN_OUT)
    triangle:addAction(action)
    action:run()

    Engine.setScene(scene)

    function onTouchStart(x, y)
        if (action:isRunning()) then
            action:pause()
        else
            action:run()
        end
    end
    Engine.onTouchPress = onTouchPress;
    ```

### Pre-defined ease functions

#### Linear
![Linear](../images/ease/linear.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(S_LINEAR);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(TimeAction.LINEAR);
    ```
#### Quad
![Quad](../images/ease/easeQuad.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(S_EASE_QUAD_IN);
    action.setFunctionType(S_EASE_QUAD_OUT);
    action.setFunctionType(S_EASE_QUAD_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(Action.EASE_QUAD_IN);
    action:setFunctionType(Action.EASE_QUAD_OUT);
    action:setFunctionType(Action.EASE_QUAD_IN_OUT);
    ```
#### Cubic
![Cubic](../images/ease/easeCubic.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(S_EASE_CUBIC_IN);
    action.setFunctionType(S_EASE_CUBIC_OUT);
    action.setFunctionType(S_EASE_CUBIC_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(Action.EASE_CUBIC_IN);
    action:setFunctionType(Action.EASE_CUBIC_OUT);
    action:setFunctionType(Action.EASE_CUBIC_IN_OUT);
    ```
#### Quart
![Quart](../images/ease/easeQuart.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(S_EASE_QUART_IN);
    action.setFunctionType(S_EASE_QUART_OUT);
    action.setFunctionType(S_EASE_QUART_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(Action.EASE_QUART_IN);
    action:setFunctionType(Action.EASE_QUART_OUT);
    action:setFunctionType(Action.EASE_QUART_IN_OUT);
    ```
#### Quint
![Quint](../images/ease/easeQuint.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(S_EASE_QUINT_IN);
    action.setFunctionType(S_EASE_QUINT_OUT);
    action.setFunctionType(S_EASE_QUINT_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(Action.EASE_QUINT_IN);
    action:setFunctionType(Action.EASE_QUINT_OUT);
    action:setFunctionType(Action.EASE_QUINT_IN_OUT);
    ```
#### Sine
![Sine](../images/ease/easeSine.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(S_EASE_SINE_IN);
    action.setFunctionType(S_EASE_SINE_OUT);
    action.setFunctionType(S_EASE_SINE_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(Action.EASE_SINE_IN);
    action:setFunctionType(Action.EASE_SINE_OUT);
    action:setFunctionType(Action.EASE_SINE_IN_OUT);
    ```
#### Expo
![Expo](../images/ease/easeExpo.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(S_EASE_EXPO_IN);
    action.setFunctionType(S_EASE_EXPO_OUT);
    action.setFunctionType(S_EASE_EXPO_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(Action.EASE_EXPO_IN);
    action:setFunctionType(Action.EASE_EXPO_OUT);
    action:setFunctionType(Action.EASE_EXPO_IN_OUT);
    ```
#### Circ
![Circ](../images/ease/easeCirc.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(S_EASE_CIRC_IN);
    action.setFunctionType(S_EASE_CIRC_OUT);
    action.setFunctionType(S_EASE_CIRC_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(Action.EASE_CIRC_IN);
    action:setFunctionType(Action.EASE_CIRC_OUT);
    action:setFunctionType(Action.EASE_CIRC_IN_OUT);
    ```
#### Elastic
![Elastic](../images/ease/easeElastic.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(S_EASE_ELASTIC_IN);
    action.setFunctionType(S_EASE_ELASTIC_OUT);
    action.setFunctionType(S_EASE_ELASTIC_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(Action.EASE_ELASTIC_IN);
    action:setFunctionType(Action.EASE_ELASTIC_OUT);
    action:setFunctionType(Action.EASE_ELASTIC_IN_OUT);
    ```
#### Back
![Back](../images/ease/easeBack.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(S_EASE_BACK_IN);
    action.setFunctionType(S_EASE_BACK_OUT);
    action.setFunctionType(S_EASE_BACK_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(Action.EASE_BACK_IN);
    action:setFunctionType(Action.EASE_BACK_OUT);
    action:setFunctionType(Action.EASE_BACK_IN_OUT);
    ```
#### Bounce
![Bounce](../images/ease/easeBounce.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(S_EASE_BOUNCE_IN);
    action.setFunctionType(S_EASE_BOUNCE_OUT);
    action.setFunctionType(S_EASE_BOUNCE_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(Action.EASE_BOUNCE_IN);
    action:setFunctionType(Action.EASE_BOUNCE_OUT);
    action:setFunctionType(Action.EASE_BOUNCE_IN_OUT);
    ```

### User-defined ease functions

It's also possible to create new functions and attach it to a TimeAction.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    float newFunction(float time){
        return time * 2;
    }

    action.setFunction(newFunction);
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    function newFunction(time)
        return time * 2
    end

    action:setFunction(newFunction);
    ```


## MoveAction

Is used to generate a movement in objects.

Class default constructor:  
**MoveAction(Vector3 startPosition, Vector3 endPosition, float duration, bool loop=false)**

=== ":octicons-file-code-16: `C++`"
    ``` c++
    action = new MoveAction(Vector3(100,200,0), Vector3(0,10,0), 2, false);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action = MoveAction(Vector3(100,200,0), Vector3(0,10,0), 2, true)
    ```

## RotateAction

Is used to generate rotation in objects. Rotations are made by quaternions, but you can easily a create quaternions with angles.

Class default constructor:  
**RotateAction(Quaternion startRotation, Quaternion endRotation, float duration, bool loop=false)**

=== ":octicons-file-code-16: `C++`"
    ``` c++
    Quaternion fromAngle;
    fromAngle.fromAngle(20);

    Quaternion toAngle;
    toAngle.fromAngle(80);

    action = new RotateAction(fromAngle, toAngle, 5, true);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    fromAngle = Quaternion()
    fromAngle:fromAngle(20)

    toAngle = Quaternion()
    toAngle:fromAngle(80)

    action = RotateAction(fromAngle, toAngle, 2, true)
    ```

For default, a Quaternion method fromAngleAxis uses axis Z (for 2D projects) to perform a rotation, but it`s also possible to make rotations for any axis:

=== ":octicons-file-code-16: `C++`"
    ``` c++
    fromAngle.fromAngleAxis(20, Vector3(0, 1, 0));
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    fromAngle:fromAngleAxis(10, Vector3(0,1,0))
    ```

## ScaleAction

Is used to change object scale. Scales are setting by Vector3. For example, if you want increase the object 3 times from Y axis you can use ```Vector3(1, 3, 1)```.

Class default constructor:  
**ScaleAction(Vector3 startScale, Vector3 endScalel, float duration, bool loop=false)**

=== ":octicons-file-code-16: `C++`"
    ``` c++
    action = new ScaleAction(Vector3(1,1,1), Vector3(1,10,1), 2, true);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action = ScaleAction(Vector3(1,1,1), Vector3(1,10,1), 2, true)
    ```

## ColorAction

Is used to change the color of object.

Class default constructor:  
**ColorAction(float startRed, float startGreen, float startBlue, float endRed, float endGreen, float endBlue, float duration, bool loop=false)**

=== ":octicons-file-code-16: `C++`"
    ``` c++
    action = new ColorAction(0, 0.5, 0.8, 1, 0.4, 0, 5, true);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action = ColorAction(0, 0.5, 0.8, 1, 0.4, 0, 5, true)
    ```

## AlphaAction

Is used to change alpha factor of object. Alpha 1.0 é full opaque object and alpha 0.0 is full transparent object.

Class default constructor:  
**AlphaAction(float startAlpha, float endAlpha, float duration, bool loop=false)**

=== ":octicons-file-code-16: `C++`"
    ``` c++
    action = new AlphaAction(1, 0, 5, true);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action = AlphaAction(1, 0, 5, true)
    ```
