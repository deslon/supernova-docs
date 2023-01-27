In Supernova to use particle system you have to two kind of tools: Particle Initializers and Particle Modifiers.

* Particle Initializers
    * Life
    * Position
    * Velocity
    * Acceleration
    * Color
    * Alpha
    * Size
    * Sprite
    * Rotation
* Particle Modifiers
    * Position
    * Velocity
    * Acceleration
    * Color
    * Alpha
    * Size
    * Sprite
    * Rotation

[Particles live sample :octicons-file-code-16:](https://samples.supernovaengine.org/particles/){ .md-button }

Here is an example how Inittializers and Modifiers can be used to create particles animation.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    #include "Supernova.h"
    using namespace Supernova;

    #include "Particles.h"
    #include "ParticlesAnimation.h"

    Scene scene;

    Particles particles(&scene);
    ParticlesAnimation partianim(&scene);

    void init(){
        particles.setMaxParticles(100);
        particles.setTexture("f4.png");
        particles.setPosition(300, 100, 0);
        partianim.setTarget(particles.getEntity());

        partianim.setRate(10);

        partianim.setLifeInitializer(10);
        partianim.setPositionInitializer(Vector3(0,0,0), Vector3(300,0,0));
        partianim.setVelocityInitializer(Vector3(0,10,0), Vector3(0,50,0));
        partianim.setColorInitializer(Vector3(0,0,0), Vector3(1,1,1));
        partianim.setSizeInitializer(10, 50);

        partianim.setVelocityModifier(5, 8, Vector3(0,10,0), Vector3(0,300,0), EaseType::CUBIC_IN_OUT);
        partianim.setAlphaModifier(4, 6, 1, 0.2);

        Engine::setScene(&scene);

        partianim.start();
    }
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    scene = Scene()

    particles = Particles(scene)
    partianim = ParticlesAnimation(scene)

    particles.maxParticles = 100
    particles:setPosition(300, 100, 0)
    particles:setTexture("f4.png")
    partianim.target = particles.entity

    partianim.rate = 10

    partianim:setLifeInitializer(10)
    partianim:setPositionInitializer(Vector3(0,0,0), Vector3(300,0,0))
    partianim:setVelocityInitializer(Vector3(0,10,0), Vector3(0,50,0))
    partianim:setColorInitializer(Vector3(0,0,0), Vector3(1,1,1))
    partianim:setSizeInitializer(10, 50)

    partianim:setVelocityModifier(5, 8, Vector3(0,10,0), Vector3(0,300,0), EaseType.CUBIC_IN_OUT)
    partianim:setAlphaModifier(4, 6, 1, 0.2)

    Engine.setScene(scene)

    partianim:start()
    ```

##Particle Initializers

###Life Initializer

Every particle has its life and this life is regressive. When a particle starts, through this class you can set the lifetime of it. Throughout the life of the particle, when it reaches 0, the particle dies.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    partianim.setLifeInitializer(10, 10);
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    partianim:setLifeInitializer(10, 10)
    ```

###Position Initializer

The initial position of particle.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    partianim.setPositionInitializer(Vector3(0,0,0), Vector3(300,0,0));
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    partianim:setPositionInitializer(Vector3(0,0,0), Vector3(300,0,0))
    ```

###Velocity Initializer

It's the initial velocity of particle.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    partianim.setVelocityInitializer(Vector3(0,10,0), Vector3(0,50,0));
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    partianim:setVelocityInitializer(Vector3(0,10,0), Vector3(0,50,0))
    ```

###Acceleration Initializer

It's to set inital acceleration of particle with this class.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    partianim.setAccelerationInitializer(Vector3(0,100,0), Vector3(0,200,0));
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    partianim:setAccelerationInitializer(Vector3(0,100,0), Vector3(0,200,0))
    ```

###Color Initializer

Can be used to set initial color of particle.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    partianim.setColorInitializer(Vector3(0,0,0), Vector3(1,1,1));
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    partianim:setColorInitializer(Vector3(0,0,0), Vector3(1,1,1))
    ```

###Alpha Initializer

It can be used to set particle transparency. When set 0 is total transparent particle, when set 1.0 is total opaque particle.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    partianim.setAlphaInitializer(0, 1);
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    partianim:setAlphaInitializer(0, 1)
    ```


###Size Initializer

Every particle can have its size. This class is used to set initial size of particle.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    partianim.setSizeInitializer(10, 50);
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    partianim:setSizeInitializer(10, 50)
    ```

###Sprite Initializer

A particle can also have behave like a sprite. The sprite of particle is set by an integer and during particle creation the initial sprite is sorted.  
In Supernova we call sprite as a rect of sprite sheet.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    std::vector<int> sprites;
    sprites.push_back(1);
    sprites.push_back(0);
    sprites.push_back(2);
    partianim.setSpriteIntializer(sprites);
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    partianim:setSpriteIntializer({1, 0, 2})
    ```

###Rotation Initializer

The initial rotation of particle is set with this class. The engine default is degress, but it can be changed.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    partianim.setRotationInitializer(90, 90);
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    partianim:setRotationInitializer(90, 90)
    ```

##Particle Modifiers

###Position Modifier

This modifier makes all particles travel from start position to end position in determined time.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    partianim.setPositionModifier(2, 4, Vector3(0,0,0), Vector3(0,300,0));
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    partianim:setPositionModifier(2, 4, Vector3(0,0,0), Vector3(0,300,0))
    ```

###Velocity Modifier

This modifier changes particle velocity in determined time.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    partianim.setVelocityModifier(5, 8, Vector3(0,10,0), Vector3(0,300,0));
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    partianim:setVelocityModifier(5, 8, Vector3(0,10,0), Vector3(0,300,0))
    ```

###Acceleration Modifier

This modifier changes acceleration in determined time.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    partianim.setAccelerationInitializer(Vector3(0,100,0), Vector3(0,200,0));
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    partianim:setAccelerationInitializer(Vector3(0,100,0), Vector3(0,200,0))
    ```

###Color Modifier

This modifier changes color particle in determined time.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    partianim.setColorModifier(2, 5, Vector3(1,1,1), Vector3(1,0,0));
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    partianim:setColorModifier(2, 5, Vector3(1,1,1), Vector3(1,0,0))
    ```

###Alpha Modifier

This modifier changes alpha from particle in determined time.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    partianim.setAlphaModifier(4, 6, 1, 0.2);
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    partianim:setAlphaModifier(4, 6, 1, 0.2)
    ```

###Size Modifier

This modifier changes size of particle in determined time.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    partianim.setSizeModifier(1, 3, 10, 50);
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    partianim:setSizeModifier(1, 3, 10, 50)
    ```

###Sprite Modifier

This modifier changes sprite animation of particle in determined time.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    partianim.setSpriteModifier(5, 8, {0,1,2});
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    partianim:setSpriteModifier(5, 8, {0,1,2})
    ```

###Rotation Modifier

This modifier changes rotation of particle in determined time.

=== ":octicons-file-code-16: `C++`"

    ``` c++
    partianim.setRotationModifier(1, 5, 0, 360);
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    partianim:setRotationModifier(1, 5, 0, 360)
    ```