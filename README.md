# unity-style
A unity style guide that addresses more Unity specific issues and avoids general C# style guidelines.

# Public variables
Define variables with attention to how they will impact the use of Unity's inspector.

If you want a variable that will be modified by users of the inspector (Potentially designers) or if you are linking to assets, set the variable as public, or serialize the field.

If a variable should not be modified by users of the inspector or linking to assets, use a property without serialization instead:

```
public string publicString { get; private set; }
```

# Folder organization
At the top, include a folder for external packages, and one for code specific to this project. If you are sharing code between projects, create a package for it and put it in the external packages section.

Often when importing assets from the asset store, they will be installed on a top level folder. Occasinially moving that folder may break scripts. It is ideal to avoid these packages.

Inside of the project specific folder, the first level of seperation should be by subject, and then folders inside of that by asset type. For instance if you developed several animal prefabs:

```
External

Project
    Cat
        Sounds
        Models
        Scripts
    Dog
        Sounds
        Models
        Scripts
    Horse
        Sounds
        Models
        Scripts
```

If assets are used by multiple subjects, (There are terriers but also labs that bark with the same sound and scripts), the ideal is to put shared elements in seperate component folders. (I would stress composition over inheritance: http://gameprogrammingpatterns.com/component.html)

```
Project
    Dogs
        Terrier
            Models
            Scripts
        Lab
            Models
            Scripts
        Barking
            Sounds
            Scripts
```
