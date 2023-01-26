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

[Actions live sample :octicons-file-code-16:](https://samples.supernovaengine.org/actions/){ .md-button }

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
| ```onStep()``` | Called at each iteration. |

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

| Components                           |
| ------------------------------------ |
| ActionComponent                      |
| TimedActionComponent                 |

Example how to use **TimeAction** to move a triangle that is activated by mouse click and positioned by onStep function:

=== ":octicons-file-code-16: `C++`"

    ``` c++
    #include "Supernova.h"
    using namespace Supernova;

    #include "Polygon.h"
    #include "TimedAction.h"

    Scene scene;
    Polygon triangle(&scene);
    TimedAction action(&scene);

    void onActionStep();
    void onMouseDown(int button, float x, float y, int mods);

    void init(){
        triangle.addVertex(0, -100);
        triangle.addVertex(-50, 50);
        triangle.addVertex(50, 50);

        triangle.setPosition(Vector3(300,300,0));
        triangle.setColor(0.6, 0.2, 0.6, 1);

        action.setDuration(10);
        action.getComponent<ActionComponent>().onStep = onActionStep;

        Engine::setScene(&scene);
        Engine::onMouseDown = onMouseDown;
    }

    void onActionStep(){
        float angle = M_PI * 2.0 * action.getValue();
        triangle.setPosition(cos(angle)*100 + 450, sin(angle)*100 + 300, 0);
    }

    void onMouseDown(int button, float x, float y, int mods){
        if (action.isRunning())
            action.pause();
        else
            action.start();
    }
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    scene = Scene()
    triangle = Polygon(scene)
    action = TimedAction(scene)

    triangle:addVertex(0, -100)
    triangle:addVertex(-50, 50)
    triangle:addVertex(Vector3(50, 50,0))

    triangle.position = Vector3(300,300,0)
    triangle:setColor(0.6, 0.2, 0.6, 1)

    action.duration = 10

    Engine.setScene(scene)

    function onActionStep()
        angle = math.pi * 2.0 * action:getValue()
        triangle:setPosition(math.cos(angle)*100 + 450, math.sin(angle)*100 + 300, 0);
    end
    action:getActionComponent().onStep = onActionStep

    function onMouseDown(button, x, y, mods)
        if (action:isRunning()) then
            action:pause()
        else
            action:start()
        end
    end
    Engine.onMouseDown = onMouseDown
    ```

Similar to the previous example, the same function can be used with **PositionAction** instead of **TimeAction**. This time it is no longer necessary to use ```onStep()```:

=== ":octicons-file-code-16: `C++`"

    ``` c++
    #include "Supernova.h"
    using namespace Supernova;

    #include "Polygon.h"
    #include "PositionAction.h"

    Scene scene;
    Polygon triangle(&scene);
    PositionAction action(&scene);

    void onMouseDown(int button, float x, float y, int mods);

    void init(){
        triangle.addVertex(0, -100);
        triangle.addVertex(-50, 50);
        triangle.addVertex(50, 50);

        triangle.setPosition(Vector3(300,300,0));
        triangle.setColor(0.6, 0.2, 0.6, 1);

        action.setFunctionType(EaseType::ELASTIC_IN_OUT);
        action.setAction(triangle.getPosition(), Vector3(0,10,0), 2, true);
        action.setTarget(triangle.getEntity());

        Engine::setScene(&scene);
        Engine::onMouseDown = onMouseDown;
    }

    void onMouseDown(int button, float x, float y, int mods){
        if (action.isRunning())
            action.pause();
        else
            action.start();
    }
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    scene = Scene()
    triangle = Polygon(scene)
    action = PositionAction(scene)

    triangle:addVertex(0, -100)
    triangle:addVertex(-50, 50)
    triangle:addVertex(Vector3(50, 50,0))

    triangle.position = Vector3(300,300,0)
    triangle:setColor(0.6, 0.2, 0.6, 1)

    action:setFunctionType(EaseType.ELASTIC_IN_OUT)
    action:setAction(triangle.position, Vector3(0,10,0), 2, true)
    action.target = triangle.entity

    Engine.setScene(scene)

    function onMouseDown(button, x, y, mods)
        if (action:isRunning()) then
            action:pause()
        else
            action:start()
        end
    end
    Engine.onMouseDown = onMouseDown
    ```

### Pre-defined ease functions

#### Linear
![Linear](../images/ease/linear.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(EaseType::LINEAR);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(EaseType.LINEAR)
    ```
#### Quad
![Quad](../images/ease/easeQuad.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(EaseType::QUAD_IN);
    action.setFunctionType(EaseType::QUAD_OUT);
    action.setFunctionType(EaseType::QUAD_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(EaseType.QUAD_IN)
    action:setFunctionType(EaseType.QUAD_OUT)
    action:setFunctionType(EaseType.QUAD_IN_OUT)
    ```
#### Cubic
![Cubic](../images/ease/easeCubic.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(EaseType::CUBIC_IN);
    action.setFunctionType(EaseType::CUBIC_OUT);
    action.setFunctionType(EaseType::CUBIC_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(EaseType.CUBIC_IN)
    action:setFunctionType(EaseType.CUBIC_OUT)
    action:setFunctionType(EaseType.CUBIC_IN_OUT)
    ```
#### Quart
![Quart](../images/ease/easeQuart.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(EaseType::QUART_IN);
    action.setFunctionType(EaseType::QUART_OUT);
    action.setFunctionType(EaseType::QUART_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(EaseType.QUART_IN)
    action:setFunctionType(EaseType.QUART_OUT)
    action:setFunctionType(EaseType.QUART_IN_OUT)
    ```
#### Quint
![Quint](../images/ease/easeQuint.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(EaseType::QUINT_IN);
    action.setFunctionType(EaseType::QUINT_OUT);
    action.setFunctionType(EaseType::QUINT_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
   action:setFunctionType(EaseType.QUINT_IN)
   action:setFunctionType(EaseType.QUINT_OUT)
   action:setFunctionType(EaseType.QUINT_IN_OUT)
    ```
#### Sine
![Sine](../images/ease/easeSine.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(EaseType::SINE_IN);
    action.setFunctionType(EaseType::SINE_OUT);
    action.setFunctionType(EaseType::SINE_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(EaseType.SINE_IN)
    action:setFunctionType(EaseType.SINE_OUT)
    action:setFunctionType(EaseType.SINE_IN_OUT)
    ```
#### Expo
![Expo](../images/ease/easeExpo.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(EaseType::EXPO_IN);
    action.setFunctionType(EaseType::EXPO_OUT);
    action.setFunctionType(EaseType::EXPO_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(EaseType.EXPO_IN)
    action:setFunctionType(EaseType.EXPO_OUT)
    action:setFunctionType(EaseType.EXPO_IN_OUT)
    ```
#### Circ
![Circ](../images/ease/easeCirc.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(EaseType::CIRC_IN);
    action.setFunctionType(EaseType::CIRC_OUT);
    action.setFunctionType(EaseType::CIRC_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(EaseType.CIRC_IN)
    action:setFunctionType(EaseType.CIRC_OUT)
    action:setFunctionType(EaseType.CIRC_IN_OUT)
    ```
#### Elastic
![Elastic](../images/ease/easeElastic.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(EaseType::ELASTIC_IN);
    action.setFunctionType(EaseType::ELASTIC_OUT);
    action.setFunctionType(EaseType::ELASTIC_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(EaseType.ELASTIC_IN)
    action:setFunctionType(EaseType.ELASTIC_OUT)
    action:setFunctionType(EaseType.ELASTIC_IN_OUT)
    ```
#### Back
![Back](../images/ease/easeBack.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(EaseType::BACK_IN);
    action.setFunctionType(EaseType::BACK_OUT);
    action.setFunctionType(EaseType::BACK_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(EaseType.BACK_IN)
    action:setFunctionType(EaseType.BACK_OUT)
    action:setFunctionType(EaseType.BACK_IN_OUT)
    ```
#### Bounce
![Bounce](../images/ease/easeBounce.png)
=== ":octicons-file-code-16: `C++`"
    ``` c++
    action.setFunctionType(EaseType::BOUNCE_IN);
    action.setFunctionType(EaseType::BOUNCE_OUT);
    action.setFunctionType(EaseType::BOUNCE_IN_OUT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action:setFunctionType(EaseType.BOUNCE_IN)
    action:setFunctionType(EaseType.BOUNCE_OUT)
    action:setFunctionType(EaseType.BOUNCE_IN_OUT)
    ```

### User-defined ease functions

It's also possible to create new functions and attach it to a TimeAction.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    float newFunction(float time){
        return time * 2;
    }

    action.getComponent<TimedActionComponent>().function = newFunction;
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    function newFunction(time)
        return time * 2
    end

    action:getTimedActionComponent().function = newFunction
    ```


## PositionAction

Is used to generate a movement in objects.

| Components                           |
| ------------------------------------ |
| ActionComponent                      |
| TimedActionComponent                 |
| PositionActionComponent              |

=== ":octicons-file-code-16: `C++`"
    ``` c++
    PositionAction action(&scene);
    action.setAction(Vector3(100,200,0), Vector3(0,10,0), 2, false);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action = PositionAction(scene)
    action:setAction(Vector3(100,200,0), Vector3(0,10,0), 2, true)
    ```

## RotationAction

Is used to generate rotation in objects. Rotations are made by quaternions, but you can easily a create quaternions with angles.

| Components                           |
| ------------------------------------ |
| ActionComponent                      |
| TimedActionComponent                 |
| RotationActionComponent              |

=== ":octicons-file-code-16: `C++`"
    ``` c++
    Quaternion fromAngle;
    fromAngle.fromAngle(20);

    Quaternion toAngle;
    toAngle.fromAngle(80);

    RotationAction action(&scene);
    action.setAction(fromAngle, toAngle, 5, true);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    fromAngle = Quaternion()
    fromAngle:fromAngle(20)

    toAngle = Quaternion()
    toAngle:fromAngle(80)

    action = RotationAction(scene)
    action:setAction(fromAngle, toAngle, 2, true)
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

| Components                           |
| ------------------------------------ |
| ActionComponent                      |
| TimedActionComponent                 |
| ScaleActionComponent                 |

=== ":octicons-file-code-16: `C++`"
    ``` c++
    ScaleAction action(&scene);
    action.setAction(Vector3(1,1,1), Vector3(1,10,1), 2, true);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action = ScaleAction(scene)
    action:setAction(Vector3(1,1,1), Vector3(1,10,1), 2, true)
    ```

## ColorAction

Is used to change the color of object.

| Components                           |
| ------------------------------------ |
| ActionComponent                      |
| TimedActionComponent                 |
| ColorActionComponent                 |

=== ":octicons-file-code-16: `C++`"
    ``` c++
    ColorAction action(&scene);
    action.setAction(Vector3(0, 0.5, 0.8), Vector3(1, 0.4, 0), 5, true);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action = ColorAction(scene)
    action:setAction(Vector3(0, 0.5, 0.8), Vector3(1, 0.4, 0), 5, true)
    ```

## AlphaAction

Is used to change alpha factor of object. Alpha 1.0 é full opaque object and alpha 0.0 is full transparent object.

| Components                           |
| ------------------------------------ |
| ActionComponent                      |
| TimedActionComponent                 |
| AlphaActionComponent                 |

=== ":octicons-file-code-16: `C++`"
    ``` c++
    AlphaAction action(&scene);
    action.setAction(1, 0, 5, true);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    action = AlphaAction(scene)
    action:setAction(1, 0, 5, true)
    ```
