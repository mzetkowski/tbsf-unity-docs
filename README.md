# Turn-Based Strategy Framework v4.0 - Unity Documentation

## 1. Introduction

The Turn-Based Strategy Framework (TBSF) is a flexible and customizable toolkit for developing turn-based strategy games. It handles essential mechanics like grid-based movement, turn management, unit behaviour, and AI decision-making, while offering the flexibility to extend and customize these systems to fit your project’s needs. With support for both Unity and Godot, TBSF gives developers the freedom to choose their preferred engine without sacrificing functionality. Proven in released games and supported by an active Discord community, TBSF offers reliability for professional projects along with a friendly space for advice, feedback, and collaboration.

## Core Features

- Covers basic turn-based mechanics, like map generation, pathfinding, combat, and special abilities.  
- Works with both hexagonal and square grids, in 2D and 3D environments.  
- Supports gameplay for both human and AI opponents.  
- Comes with built-in online multiplayer functionality.  
- Used in real-world projects with an active community for help and feedback.

## Who Should Use This Framework?

The Framework is designed for Unity and Godot developers who want to save time on implementing basic turn-based mechanics and focus on quickly prototyping and building gameplay features. It handles the core systems so you can concentrate on what makes your game unique. It’s suitable for both experts and beginners with basic C# programming skills, offering flexibility for experienced developers while remaining accessible to those just starting out.

## What You Will Find in This Documentation

This documentation provides a thorough guide to using the TBS Framework, from initial setup to advanced customization. You will find:

- Step-by-step instructions for setting up your project in Unity or Godot.
- In-depth explanations of core concepts such as cells, units, grids, and player interactions.
- Guidance on customizing and extending the framework to suit your specific game design needs.
- A detailed look at the AI system, along with strategies for creating intelligent and adaptable opponents.
- Setting up online play
- Tutorials, examples, and best practices to help you get the most out of the framework.

The goal of this documentation is to equip you with the knowledge needed to efficiently build and expand your turn-based strategy game, using a powerful and flexible framework that adapts to your creative vision.

## Table Of Contents

* [1. Introduction](#1-introduction)
   * [Core Features](#core-features)
   * [Who Should Use This Framework?](#who-should-use-this-framework)
   * [What You Will Find in This Documentation](#what-you-will-find-in-this-documentation)
* [2. Getting Started](#2-getting-started)
   * [Prerequisites](#prerequisites)
   * [Installation and Setup](#installation-and-setup)
   * [Project Structure Overview](#project-structure-overview)
   * [Running samples](#running-samples)
* [3. Scene Structure](#3-scene-structure)
   * [Scene Hierarchy Overview](#scene-hierarchy-overview)
* [4. Creating a Scene](#4-creating-a-scene)
   * [What is a Cell?](#what-is-a-cell)
   * [What is a Unit?](#what-is-a-unit)
   * [Introduction to the GridHelper](#introduction-to-the-gridhelper)
   * [Grid Generation Fields and Parameters](#grid-generation-fields-and-parameters)
   * [Working with the Generated Scene](#working-with-the-generated-scene)
   * [Tile Painter](#tile-painter)
   * [Unit Painter](#unit-painter)
   * [Using Unity's Tile Palette with Custom Brushes](#using-unitys-tile-palette-with-custom-brushes)
* [5. Customization](#5-customization)
   * [Cell Customization](#cell-customization)
   * [Unit Customization](#unit-customization)
   * [Highlighter System](#highlighter-system)
* [6. Unit Ability System](#6-unit-ability-system)
   * [Overview of Ability Class Methods](#overview-of-ability-class-methods)
   * [Executing Abilities](#executing-abilities)
   * [Setting up Abilities](#setting-up-abilities)
   * [Sample Abilities](#sample-abilities)
* [7. AI System](#7-ai-system)
   * [AIPlayer and Unit Selection](#aiplayer-and-unit-selection)
   * [Behaviour Trees and Nodes](#behaviour-trees-and-nodes)
* [8. Game State Management](#8-game-state-management)
   * [User Interaction](#user-interaction)
   * [Turn Management](#turn-management)
   * [Ending the Game](#ending-the-game)
* [9. Online Multiplayer](#9-online-multiplayer)
   * [Architecture](#architecture)
   * [Scene Setup](#scene-setup)
   * [Network GUI](#network-gui)
   * [Game State Synchronization](#game-state-synchronization)
   * [Additional Actions](#additional-actions)
   * [Nakama Integration](#nakama-integration)
* [10. Tutorial](#9-tutorial)
   * [Cell Template](#cell-template)
   * [Generating the Grid Using the Grid Helper](#generating-the-grid-using-the-grid-helper)
   * [Creating an Obstacle Cell](#creating-an-obstacle-cell)
   * [Painting Obstacles onto the Grid](#painting-obstacles-onto-the-grid)
   * [Creating the Unit Template](#creating-the-unit-template)
* [11. Beyond the Basics: Pushing the Limits of the Turn-Based Strategy Framework](#11-beyond-the-basics-pushing-the-limits-of-the-turn-based-strategy-framework)
   * [1. Using Unity Tilemap System for maps](#1-using-unity-tilemap-system-for-maps)
   * [2. Porting to other engines](#2-porting-to-other-engines)
* [12. Support](#12-support)
* [13. Conclusion](#13-conclusion)

## 2. Getting Started
### Prerequisites
The Framework was designed to be used with Unity 2023 and above

### Installation and Setup
Follow these steps to import the Turn Based Strategy Framework into your project:

1. Navigate to the Framework page on the Unity Asset Store at https://u3d.as/mfd
2. Press the "Open in Unity" button
3. In the Package Manager window, press the "Download" button and then "Import" button
4. In the Import dialog window, press the "Next" button
   
   **OR**

1. Open Package Manager in the Unity Editor
2. Search for the "Turn Based Strategy Framework"
3. In the Package Manager window, press the "Download" button and then "Import" button
4. In the Import dialog window, press the "Next" button

### Project Structure Overview
The TBS Framework is organized to be clear and easy to use. This page describes the main parts of the project and how they are set up.

* The **`Editor/`** folder contains editor-specific scripts and tools, like the Grid Helper.
* The **`Examples/`** folder contains sample scenes, assets, and code demonstrating framework usage, including the tutorial.
* The **`External/tbsf-common/`** folder houses the core framework logic shared across engines.
* Finally, the **`Scripts/`** folder contains Unity-specific implementations of framework components and game logic.
  
```
TBSF/
├───Editor                                  # Editor-specific scripts and tools, like the Grid Helper
├───Examples                                # Sample scenes, assets, and code demonstrating framework usage, including the tutorial
├───External
│   └───tbsf-common                         # Core framework logic shared across engines
└───Scripts                                 # Unity-specific implementations of framework components and game logic
```
<div align="center"><i>TBSF project structure</i></div>

### Running samples
The best way to get familiar with the framework is to study the sample demos provided. These examples showcase various features and configurations, helping you understand how to integrate and utilize the framework in your own projects.

The `Examples` folder contains several types of demos:

* **Clash of Heroes Demo**: A comprehensive demonstration showcasing many framework features working together.
* **Legacy Demos**: Simpler demonstrations from previous versions of the framework, still valuable for understanding core concepts.
* **Tilemap Demo**: A demo showcasing an alternative grid setup using Unity's Tilemap system.

To run these examples and quickly get familiar with the framework:

1.  Navigate to any demo in the `Examples/` folder in your Unity project's Project window.
2.  Double-click on any of the scene files to open them in the Unity Editor.
3.  Press the **Play** button in the Unity Editor to start the scene and interact with the demo.

## 3. Scene Structure
### Scene Hierarchy Overview
This section covers the structure of a bare-bones scene in the Turn-Based Strategy Framework. The following hierarchy represents the minimal setup required for a playable scene. More complex levels with custom game mechanics might include additional components.

```
Root
│
├── CellManager/          // RegularCellManager.cs, assigned to Grid Controller
│   └── Cells
│
├── UnitManager/          // UnityUnitManager.cs, assigned to Grid Controller
│   └── Units
│
├── PlayerManager/        // UnityPlayerManager.cs, assigned to Grid Controller
│   └── Players
│
├── GridController/       // UnityGridController.cs 
│   └── TurnResolver      // Assigned to Grid Controller
│
├── GUIController/        // GUIController.cs
│
├── Camera
│   └── Physics Raycaster // For mouse interaction with the game
│
└── GameEndConditions/
    └── Conditions
```
<div align="center"><i>Basic scene structure</i></div>

- **CellManager**:  
  The `CellManager` handles all cells within the grid. It allows retrieval of specific cells and marking cells for visual feedback (such as highlighting selected or reachable cells). All cells in the game are added as children of the `CellManager` game object.

- **UnitManager**:  
  The `UnitManager` oversees all units, enabling unit addition and retrieval of friendly or enemy units based on the player. It also handles visual indicators like marking units as selected, finished, or attacking. All units in the game are added as children of the `UnitManager` game object.

- **PlayerManager**:  
  The `PlayerManager` manages all players in the game, offering methods to retrieve players and identify them by player number. All player game objects are added as children of the `PlayerManager` game object.

- **GridController**:  
  The `GridController` is the core of the grid-based gameplay. It orchestrates interactions between cells, units, and players. It also manages key game functions like turn progression, ensuring that each player gets a turn and that the game moves smoothly from one turn to the next. The `GridController` references the `TurnResolver` to manage turn transitions and interacts with the managers (`CellManager`, `UnitManager`, `PlayerManager`) to keep track of the game's state.

- **TurnResolver**:  
  This component handles the progression of turns in the game. It determines which player goes next and manages the transition between player turns. The `TurnResolver` can be customized to fit specific game rules, allowing developers to implement custom turn mechanics.

- **GUI Controller**:  
  A basic component that handles ending player's turn at the press of a button on the keyboard. 

- **GameEndConditions**:  
  This component defines the victory or loss conditions for the game. By default, the `DominationCondition` is used, which checks if only one player has remaining units, ending the game if true. Custom conditions can be added to tailor the game’s end state to specific rules, like capturing objectives or achieving a score threshold.

## 4. Creating a Scene
Before proceeding with grid generation, it’s essential to understand two core concepts: **cells** and **units**. These are the fundamental building blocks of your game’s grid. In the next sections, we’ll explain what cells and units are, and how they interact with the grid to create engaging turn-based strategy gameplay.

### What is a Cell?
In the Turn-Based Strategy Framework, a **cell** is the fundamental building block of the game’s grid. Each cell represents a tile on the map, and together, cells form the entire game board where the action takes place. The Framework provides two ready-to-use implementations of the abstract `Cell.cs` class—`Hexagon.cs` for hexagonal grids and `Square.cs` for square grids.

A cell is a GameObject with one of these scripts, or a custom script derived from `Cell.cs`, attached to it. A typical cell includes a 3D model or sprite and a **Collider** component for handling mouse interactions. To enable interaction, you'll use Unity's Event System with a **Physics Raycaster** on the camera, and the cell script implements the `IPointerClickHandler`, `IPointerEnterHandler`, and `IPointerExitHandler` interfaces. Finally, a cell has functions that define its appearance in different game states (e.g., selected, reachable, or part of a path). To complete the cell setup, these functions should be assigned to appropriate fields in the Cell script. If they’re not, the cell will provide no visual feedback for player actions. The project includes several predefined highlighters that can be used with both cells and units. These will be discussed in the customization chapter.

> Although this is the case for the default setup of a cell, Cells don’t necessarily have to be GameObjects—see Chapter 10 for more advanced approaches like tilemap-backed virtual cells.

Each cell has several important properties: its **GridCoordinates** define its position on the grid, while **WorldPosition** refers to its location in the 3D game world. A cell can also be marked as **IsTaken**, indicating whether it’s occupied, and it keeps track of units within it through **CurrentUnits**, a list of any occupying units. Additionally, **MovementCost** determines the cost of moving to the cell.

```
Root (GameObject)                        // `Hexagon.cs`, `Square.cs`, or a custom derived script attached
│
├── Collider                             // Contains a Collider component (e.g., Box Collider, Mesh Collider)
│
├── MeshRenderer / SpriteRenderer        // The model or sprite representing the cell
│
└── Highlighters (GameObject)            // Container for visual feedback for different states, contains implementations of `Highlighter.cs`
    ├── UnMarkHighlighter                // GameObject with a Highlighter script to restore default appearance
    ├── SelectedHighlighter              // GameObject with a Highlighter script for selection
    ├── ReachableHighlighter             // GameObject with a Highlighter script for reachable cells
    └── PathHighlighter                  // GameObject with a Highlighter script for movement paths
```
<div align="center"><i>Basic structure of a typical cell</i></div>

### What is a Unit?
In the Turn-Based Strategy Framework, a **unit** represents an entity that players control or interact with on the grid. Units are the main actors in gameplay, capable of moving between cells, engaging in combat, and using special abilities. The framework allows for customization of units to support different gameplay mechanics.

Several fields define a unit's capabilities: **ActionPoints** determine how many actions a unit can perform per turn, while **MovementPoints** define how far the unit can move. Units also have **Health**, which affects their survivability, **AttackRange**, which determines their attack distance, and **AttackFactor** and **DefenceFactor**, which influence how much damage they deal and how much they can defend against.

A Unit is a GameObject with the `Unit.cs`, or derived, script attached to it. A typical unit GameObject structure includes a model or sprite representing the unit and a **Collider** component for handling interactions. To enable interaction, you'll use Unity's Event System with a **Physics Raycaster** on the camera, and the unit script implements the `IPointerClickHandler`, `IPointerEnterHandler`, and `IPointerExitHandler` interfaces. Units also include visual indicators for different states, such as being selected, engaged in combat, or marked as a target. To complete the unit setup, these functions should be assigned to the relevant fields in the `Unit` script to ensure visual feedback in different game states.

Apart from that, a unit typically has two default abilities—**MoveAbility** and **AttackAbility**. These abilities are assigned to the `BaseAbilities` field on the Unit script. **Base abilities** are the abilities that get activated by default when a unit is selected, allowing it to move across the grid or attack other units. If no ability is assigned to the `BaseAbilities` field, the unit will not be able to take any action.

Finally, each unit has a "brain" GameObject that holds a **BehaviourTreeResource**. This component lets the AI control the unit's actions and decision-making. The project includes a simple `RegularBehaviourTree` you can use, or you can set up your own custom trees (covered in a later chapter). `BehaviourTreeResource` should be assigned to `Unit._behaviourTreeNode` in the editor.

```
Root (GameObject)                        // `Unit.cs` or a custom derived script attached
│
├── Collider                             // Contains a Collider component (e.g., Box Collider, Mesh Collider)
│
├── MeshRenderer / SpriteRenderer        // The model or sprite representing the unit
│
├── Highlighters (GameObject)            // Container for visual feedback for different states
│   ├── MarkAsSelectedHighlighter        // GameObject with a Highlighter script for selected state
│   ├── MarkAsFriendlyHighlighter        // GameObject with a Highlighter script for friendly state
│   ├── MarkAsFinishedHighlighter        // GameObject with a Highlighter script for finished state
│   ├── MarkAsReachableEnemyHighlighter  // GameObject with a Highlighter script for reachable enemy state
│   └── MarkAsAttackingHighlighter       // GameObject with a Highlighter script for attacking state
│                      
├── MoveAbility (GameObject)             // GameObject with MoveAbility script
├── AttackAbility (GameObject)           // GameObject with AttackAbility script
│
└── Brain (GameObject)                   // BehaviourTreeNode script/component used by the AI to control the unit
```
<div align="center"><i>Basic structure of a typical unit</i></div>

### Introduction to the GridHelper

The **GridHelper** is a tool in the Turn-Based Strategy Framework that automates the creation of grid-based maps. It allows you to set up a grid, assign cells, and place units on it, simplifying the process of building your game’s levels.

To begin using the **GridHelper** for generating grids in Unity, simply select **Window > Grid Helper** in the Unity Editor. The Grid Helper window will appear.

### Grid Generation Fields and Parameters

The **GridHelper** provides several fields that allow you to customize your grid’s size, shape, and the types of cells and units it will contain. Below are the parameters available for grid generation:

- **Human Players No**:  
  This field allows you to specify the number of human players in the game. The default value is `2`, but you can adjust it depending on your game’s requirements.

- **AI Players No**:  
  Here, you can set the number of AI-controlled players that will participate in the game.

  The number of players can be changed after the grid is generated by adding or removing player nodes from the **PlayerManager** node.

- **Plane**:
Indicates whether the map should be generated along the XY (for 2D maps) or XZ plane (for 3D maps)

- **Generator**:
  Select the generator for either Square based maps or Hex based maps

- **Width and Height**:  
  These fields determine the dimensions of the grid. You can set both the **width** (number of columns) and **height** (number of rows) to customize the size of your map.

- **Cell Prefab**:  
  This field allows you to assign a specific cell prefab to be used for generating the grid.

To generate the map, do the following:
  - Create a new scene using **File > New Scene**
  - Fill in the Grid Helper parameters
  - Click the **Generate Scene** button 

The script will automatically create all necessary components described in the previous chapter, including the **CellManager**, **PlayerManager**, and **UnitManager**. It will also ensure that a main camera is placed in the scene and properly aligned to show the grid. Additionally, the script will add lighting and a basic GUI controller for handling turn transitions.

### Working with the Generated Scene

Once the grid is generated, you can make adjustments to the scene using two primary methods for map editing: the dedicated Painters within the Grid Helper, and Unity's Tile Palette with custom brushes.

* **Editing the Map**:
    * **Using Painters (Legacy)**: The **Tile Painter** is a legacy feature that allows you to customize the grid by applying different cell types, and the **Unit Painter** is used to place and assign units. **Note:** With painters, you can only paint over cells that have already been generated by the Grid Helper.
    * **Using Unity's Tile Palette (New)**: For a more integrated workflow, you can use Unity's **Tile Palette** with custom `CellBrush` and `UnitBrush` assets to paint cells and units directly onto the grid. A key advantage of this new method is the ability to add cells arbitrarily, not just replace existing ones.

* **Managing Players**: Players are managed by adding or removing player GameObjects under the **PlayerManager** GameObject. Ensure each player GameObject is properly configured with an appropriate player number.

### Tile Painter

The **Tile Painter** is a tool within the **GridHelper** that allows you to modify the generated grid by applying different cell types to specific locations. This can be useful for customizing parts of the map, such as designating obstacles or other terrain features.

To use the Tile Painter:

1.  **Assign a Cell Prefab**: Assign the cell prefab you want to paint with to the **Cell Prefab** field in the **GridHelper** window.
2.  **Enter Tile Edit Mode**: Click the **Enter Tile Edit Mode** button. This activates the painting mode.
3.  **Painting Cells**: While in tile edit mode, click on any cell in the grid to replace it with the selected cell prefab. The new cell will take the place of the existing one.
4.  **Exit Tile Edit Mode**: Once you’ve finished making changes, click the **Exit Tile Edit Mode** button to return to the normal scene editing mode.

### Unit Painter

The **Unit Painter** allows you to place and assign units to specific players on the grid. This tool is helpful for setting up the initial state of the game, such as positioning starting units for each player or placing neutral units.

To use the Unit Painter:

1.  **Assign a Unit Prefab**: Assign the unit prefab to the **Unit Prefab** field in the **GridHelper** window.
2.  **Assign Player Number**: Set the **Player Number** field to the player you want to assign the unit to. This number corresponds to the player GameObject in the **PlayerManager**.
3.  **Enter Unit Edit Mode**: Click the **Enter Unit Edit Mode** button to activate unit placement mode.
4.  **Placing Units**: While in unit edit mode, click on a cell in the grid to place a unit. The unit will be positioned on the selected cell and assigned to the player you specified.
5.  **Exit Unit Edit Mode**: After placing the units, click the **Exit Unit Edit Mode** button to return to the normal scene editing mode.

### Using Unity's Tile Palette with Custom Brushes

The framework provides custom brushes (`CellBrush` and `UnitBrush`) to integrate map editing directly with Unity's Tile Palette system. This offers a more flexible and familiar workflow for Unity developers.

To use the custom brushes with the Tile Palette:

1.  **Select the Grid GameObject**: In your scene's Hierarchy window, select the `Grid` GameObject (this is the GameObject where the `GridController` script is attached).
2.  **Open the Tile Palette Window**: Navigate to **Window > 2D > Tile Palette** in the Unity Editor.
3.  **Select a Custom Brush**: In the Tile Palette window, select either the `CellBrush` or `UnitBrush` from the dropdown. These are custom brush assets provided with the framework.
4.  **Assign Prefabs**:
    * If using `CellBrush`, assign your desired cell prefab to the **Cell Prefab** field on the brush inspector.
    * If using `UnitBrush`, assign your desired unit prefab to the **Unit Prefab** field on the brush inspector.
    * *Note*: The `UnitBrush` also has a **Player Number** field to assign the player ownership to the units you paint.
5.  **Configure Brush Parameters**: Both custom brushes have two important parameters:
    * **Offset**: This parameter changes the position of spawned cells/units relative to the grid cell's center. Adjust this to align your prefabs correctly.
    * **Is 2D Map**: Ensure this boolean parameter is set correctly based on whether your grid is a 2D or 3D map.
6.  **Paint on the Scene**: With the correct brush, prefab, and parameters set, use the Tile Palette interface (e.g., paint tool, erase tool, fill tool) to paint cells or place units directly onto your grid in the Scene view.

## 5. Customization

In the Turn-Based Strategy Framework, both cells and units can be customized in two main areas: **visuals** and **behaviour**. Below, we break down how these aspects can be modified to fit your game’s needs.

### Cell Customization
#### Cell Visuals
Cells use a series of virtual `MarkAs...` methods to control how they are visually highlighted in different game states. These methods include:

- `MarkAsHighlighted()`: Highlights the cell to indicate it is currently selected.
- `MarkAsReachable()`: Highlights the cell to show that it is reachable for movement.
- `MarkAsPath()`: Marks the cell as part of a calculated movement path, visually indicating the path a unit will take.
- `UnMark()`: Restores the cell to its default appearance, removing any visual highlights or markings.

Each of these methods is backed by a **Highlighter** object, which encapsulates the actual function used for highlighting. The user can customize the appearance of cells in two ways:
1. **Override the virtual methods**: Legacy, less flexible method that allows for complete control over how the cell behaves visually.
2. **Assign predefined highlighter objects**: The framework provides several reusable **Highlighter** objects that can be assigned to the relevant fields.

The highlighter system is flexible and shared between both units and cells, making it easy to reuse or modify the visual feedback across both.

#### Cell Behaviour

For cells, behaviour customization typically revolves around pathfinding. The following methods control how the cell interacts with other cells in the grid:

- **GetDistance(ICell otherCell)**: Determines the distance between the current cell and another cell.
- **GetNeighbours(ICellManager cellManager)**: Retrieves the neighboring cells based on the current grid configuration.

The default cell implementations, `Square.cs` and `Hexagon.cs` has both of these methods implemented.

### Unit Customization
#### Unit Visuals

Similar to cells, units rely on virtual `MarkAs...` methods to control their visual feedback in different states:

- `MarkAsSelected()`: Highlights the unit to indicate it has been selected by the player for actions.
- `MarkAsFriendly()`: Highlights the unit as friendly, to distinguish between allied and enemy units.
- `MarkAsFinished()`: Marks the unit as having completed all its actions for the turn.
- `MarkAsReachableEnemy()`: Highlights enemy units that are within range and can be targeted or attacked.
- `MarkAsAttacking()`: Visually indicates that the unit is performing an attack.
- `UnMark()`: Removes all highlights from the unit, restoring its default appearance.

These methods are also backed by **Highlighter** objects, providing the same flexibility for visual customization. As with cells, users can either override these methods or assign predefined highlighters to the corresponding fields.

#### Unit Behaviour

Units have more extensive behavioral customization options compared to cells, as they manage movement, combat, and interactions with the grid. Here are the key virtual methods you can customize:

- **Initialize()**: This method is called when the unit is created and can be used to set up initial state.
- **OnTurnStart(GridController gridController)**: Triggered at the beginning of the unit’s turn.
- **OnTurnEnd(GridController gridController)**: Triggered at the end of the unit’s turn.
- **OnUnitSelected(GridController gridController)**: Handles logic when a unit is selected by the player.
- **OnUnitDeselected(GridController gridController)**: Handles logic when a unit is deselected.
- **OnDestroyed(GridController gridController)**: Called when unit is destroyed, typically when health drops to 0.

**Movement-related methods**:
These three high-level methods used to define how the unit moves. Easy to use and should cover most of the use cases
- **IsCellMovableTo(ICell cell)**: Determines if the unit can move to a specific cell.
- **IsCellTraversable(ICell source, ICell destination)**: Checks whether a cell is traversable by the unit.
- **GetMovementCost(ICell source, ICell destination)**: Determines the movement cost between the two cells. By default, the `MovementCost` of the destination cell is considered. 

These two low-level methods allow for more precise control of unit movement. They should be used when the other three methods are not expressive enough.
- **GetAvailableDestinations(IEnumerable<ICell> cells)**: Provides a list of available destinations for the unit.
- **GetGraphEdges(ICellManager cellManager)**: Returns the graph representation of the movement grid, used by the pathfinding algorithm.

**Combat-related methods**:
- **IsUnitAttackable(IUnit otherUnit, ICell otherUnitCell, ICell attackSourceCell)**: Determines if another unit is attackable.
- **CalculateDamageDealt(IUnit aggressor)**: Calculates the damage dealt when attacking another unit.
- **CalculateDamageTaken(IUnit aggressor)**: Calculates the damage taken when attacked by another unit.


In addition to the methods above, units use a flexible ability system and a behaviour tree-based AI, which will be discussed in separate chapters.

### Highlighter System
The **Highlighter** system in the Turn-Based Strategy Framework offers a flexible way to manage visual feedback for both units and cells. Highlighters are reusable components that define how game objects visually respond to interactions like selection, movement, or combat.

Both **Cell** and **Unit** scripts contain a set of `MarkAs...Fn` fields to trigger various visual states (e.g., selected, reachable, or attacking). To use the highlighter system, simply assign a **GameObject** with a script derived from **Highlighter** to these fields. This setup is typically done by adding highlighter scripts to the prefab and linking them to the corresponding field. Multiple highlighters can be applied to a single field to create complex effects. You can create custom effects by extending the **Highlighter** class and overriding the `Apply` method, or use one of the predefined effects included in the project:

* **DebugHighlighter**
    A simple highlighter that prints a message to the console when applied. Useful for testing and debugging without any visual effects.

* **SpriteRendererHighlighter**
    This highlighter adjusts the color of a `SpriteRenderer` component by modifying its `color` property.

* **RendererHighlighter**
    This highlighter changes the color of a `MeshRenderer` component by modifying its material's shader parameters (e.g., `_Color` property).

* **GameObjectsActivatorHighlighter**
    This highlighter activates or deactivates a list of specified GameObjects, useful for toggling complex visual effects.

* **SwayHighlighter**
    Applies a sway animation to the target, moving it slightly based on its direction relative to another object. It's ideal for combat interactions, such as visually indicating a unit has been attacked or is defending.

* **ArrowSpritePathHighlighter**
    Uses directional arrow and line sprites to represent a movement path visually. It's perfect for showing how a unit will move across the grid, with arrows pointing the way.

You can find these and other highlighter scripts in the `Scripts/Highlighters/` folder. The highlighters listed above are just a few examples of the effects included in the project.

## 6. Unit Ability System
In the Turn-Based Strategy Framework, **abilities** are actions that units can perform during gameplay, such as moving, attacking, casting spells or using any other special skill. Each ability defines how a unit interacts with the grid and other units.
 
Abilities are defined using the **IAbility** interface, which outlines the core methods and behaviors that all abilities must implement. This includes methods for initializing the ability, displaying visual indicators, and handling events such as unit or cell selection. In Unity, the `Ability` class implements the `IAbility` interface and it should be extended for implementing custom skills.

### Overview of Ability Class Methods

The `Ability` class provides several virtual methods that define how a unit's ability behaves during various interactions and game phases. Depending on your custom ability’s needs, you can choose to override only the methods that are relevant, while leaving others as they are.

##### Initialization and Cleanup

- **`Initialize(GridController gridController)`**:  
  Called once when the ability is registered by the unit. Use this method to set up any initial states or prepare resources for the ability.

- **`Display(GridController gridController)`**:  
  This method is responsible for showing the ability’s effects on the grid, such as highlighting cells or units. You would typically use this to display ranges or target areas.

- **`CleanUp(GridController gridController)`**:  
  Removes any visual indicators or temporary effects left over from the ability’s display phase. This helps to reset the grid to its default state after the ability is used or canceled.

##### Unit Interaction Methods

- **`OnUnitClicked(IUnit unit, GridController gridController)`**:  
  Called when a unit is clicked while the ability is active. It’s useful for targeting specific units with abilities like attacks or buffs.

- **`OnUnitHighlighted(IUnit unit, GridController gridController)`**:  
  Triggered when a unit is highlighted while the ability is selected, allowing for visual feedback when hovering over targetable units.

- **`OnUnitDehighlighted(IUnit unit, GridController gridController)`**:  
  This method is triggered when a unit is no longer highlighted, typically used to remove any hover effects.

- **`OnUnitDestroyed(GridController gridController)`**:  
  Called when the unit that owns this ability is destroyed. This is useful for cleaning up ongoing effects or stopping the ability’s logic.

##### Cell Interaction Methods

- **`OnCellClicked(ICell cell, GridController gridController)`**:  
  This method is triggered when a cell is clicked while the ability is active.

- **`OnCellHighlighted(ICell cell, GridController gridController)`**:  
  Called when a cell is highlighted or selected, allowing you to provide visual feedback or logic based on cell interactions.

- **`OnCellDehighlighted(ICell cell, GridController gridController)`**:  
  Triggered when a cell is deselected. This is often used to remove visual effects from previously highlighted cells.

##### Turn-based Methods

- **`OnTurnStart(GridController gridController)`**:  
  Called at the beginning of the unit’s turn.

- **`OnTurnEnd(GridController gridController)`**:  
  This method is called at the end of the unit’s turn.

##### Ability Selection

- **`OnAbilitySelected(GridController gridController)`**:  
  Triggered when the ability is selected by the player or AI.

- **`OnAbilityDeselected(GridController gridController)`**:  
  Called when the ability is no longer the active one.

##### Other

- **`CanPerform(GridController gridController)`**:  
  This method is used for determining whether the ability can be used at the current moment. It evaluates conditions like action points, cooldowns, or specific game rules. If true is returned, the ability can be performed; otherwise, it cannot. Its primary role is to check if the unit can perform any more actions, and if not, the unit is marked as finished for the turn.

### Executing Abilities

In the Turn-Based Strategy Framework, abilities are executed using a **command pattern**, where each ability is represented by a `Command` object that encapsulates the action to be performed. Simply speaking, the command defines what actually happens when the ability is executed. This pattern allows for flexible execution and easy undo/redo functionality if needed. To create custom commands, implement the `ICommand` interface by overriding its `Apply` and `Undo` methods. The project includes `MoveCommand` and `AttackCommand` that can potentially be used with custom abilities.

Finally, there are two helper methods in the `Unit` class to execute actions: `HumanExecuteAbility` for human players and `AIExecuteAbility` for AI-controlled units. There is also a low-level `ExecuteAbility` method that allows defining functions to be called before and after the ability is executed. The code below illustrates both concepts:

```csharp
public class AttackAbilityImpl : IAbility<AttackCommand>
{
    /*...*/

    public void OnUnitClicked(IUnit unit, GridController gridController)
    {
        if (UnitReference.ActionPoints > 0 && _attackableUnits.Contains(unit))
        {
            UnitReference.HumanExecuteAbility(new AttackCommand(unit, UnitReference.CalculateTotalDamage(unit)), gridController);
        }

        /*...*/
    }

    /*...*/
}
```

### Setting up Abilities

In the Turn-Based Strategy Framework, abilities can be assigned to units to define the actions they can perform, such as moving, attacking, or casting spells. The abilities that should be auto-selected when the unit is selected are typically attached directly as components to the unit's GameObject. The unit automatically loads these abilities during its initialization and assign them to the `BaseAbilities` property. When the unit is initialized, it calls `RegisterAbility` on each of the abilities to assign relevant fields, hook up events, and call their `Initialize` method. Only registered abilities will function during gameplay.

It is also possible to create compound abilities that act as containers for other abilities. For example, a spellbook ability might allow the player to choose a specific spell from a list of options. In such cases, the compound ability must handle the registration of its child abilities manually.
  
### Sample Abilities
In this section, we will walk through the creation of two custom abilities to showcase key concepts in the Turn-Based Strategy Framework's ability system. The first ability, the **FireballAbility** is an area of effect attack that damages all units within given radius, the other ability, the **CompoundAbility** that allows to select a one of the abilities from a list, such as a spellbook or a menu.

#### The FireballAbility
The FireballAbility works as follows:

- When the player hovers over a cell, all cells within a defined radius (set by the _radius field) are highlighted using the MarkAsReachable method, and all units within those cells are selected.
- If the player clicks a highlighted cell, the ability applies damage to all units in the selected area using the `MultipleTargetAttackCommand`.
- The ability includes handling for dehighlighting cells and units when they are no longer being hovered over or when the ability is canceled.

##### Highlighting Cells and Units
When the player hovers over a cell, the `OnCellHighlighted` method is called. This method calculates all cells within the radius using the cell’s `GetDistance` method and highlights them using the MarkAsReachable method:
```csharp
_cellsInRange = gridController.CellManager.GetCells().Where(c => c.GetDistance(cell) <= _radius);
gridController.CellManager.MarkAsReachable(_cellsInRange);
```
Simultaneously, the units within these cells are highlighted as potential targets, even if they are friendly:
```csharp
_unitsInRange = _cellsInRange.SelectMany(c => c.CurrentUnits).ToList();
gridController.UnitManager.MarkAsReachableEnemy(_unitsInRange);
```

##### Executing the ability
When the player clicks on a highlighted cell, the `OnCellClicked` method executes. This method selects all units in the targeted area and executes the ability by invoking the `HumanExecuteAbility` method. This method uses the `MultipleTargetAttackCommand` to apply damage to all affected units:
```csharp
UnitReference.HumanExecuteAbility(new MultipleTargetAttackCommand(unitsInRange, _damage), gridController);
```
The MultipleTargetAttackCommand iterates through the units in range, applying the specified amount of damage:
```csharp
foreach (var target in _targets)
{
    target.ModifyHealth(-_damage, unit);
}
```
##### Canceling the Ability
Every ability needs to include a way to deselect it. Usually, this is done by setting a `GridStateAwaitInput` or `GridStateUnitSelected` object to the `GridController.GridState` field. In this case, when a friendly unit is clicked it is selected and therefore the FireballAbility is canceled:
```csharp
if (gridController.UnitManager.GetFriendlyUnits(unit.PlayerNumber).Contains(unit))
{
    gridController.GridState = new GridStateUnitSelected(unit, unit.GetBaseAbilities());
}
```
Alternatively, a common way to cancel a special ability is to include a cancel button in your UI and assign `GridStateAwaitingInput` to the grid state.

##### Cleaning Up After the Ability
The OnCellDehighlighted and CleanUp methods ensure that once the ability is used or canceled, all highlighted cells and units return to their default states:
```csharp
gridController.CellManager.UnMark(_cellsInRange);
gridController.UnitManager.UnMark(_unitsInRange);
```
##### Full code
```csharp
public class FireballAbility : Ability
{
    [SerializeField] private int _radius = 2;
    [SerializeField] private int _damage = 10;
    private IEnumerable<ICell> _cellsInRange;
    private IEnumerable<IUnit> _unitsInRange;

    public override void OnCellHighlighted(ICell cell, GridController gridController)
    {
        _cellsInRange = gridController.CellManager.GetCells().Where(c => c.GetDistance(cell) <= _radius);
        gridController.CellManager.MarkAsReachable(_cellsInRange);
        _unitsInRange = _cellsInRange.SelectMany(c => c.CurrentUnits).ToList();
        gridController.UnitManager.MarkAsReachableEnemy(_unitsInRange);
    }

    public override void OnCellClicked(ICell cell, GridController gridController)
    {
        var unitsInRange = _cellsInRange.SelectMany(c => c.CurrentUnits).ToList();
        UnitReference.HumanExecuteAbility(new MultipleTargetAttackCommand(unitsInRange, _damage), gridController);
    }

    public override void OnUnitClicked(IUnit unit, GridController gridController)
    {
        if (gridController.UnitManager.GetFriendlyUnits(unit.PlayerNumber).Contains(unit))
        {
            gridController.GridState = new GridStateUnitSelected(unit, unit.GetBaseAbilities());
        }
    }

    public override void OnCellDehighlighted(ICell cell, GridController gridController)
    {
        gridController.CellManager.UnMark(_cellsInRange);
        gridController.UnitManager.UnMark(_unitsInRange);
    }

    public override void CleanUp(GridController gridController)
    {
        gridController.CellManager.UnMark(_cellsInRange);
        gridController.UnitManager.UnMark(_unitsInRange);
    }

    class MultipleTargetAttackCommand : ICommand
    {
        private readonly IEnumerable<IUnit> _targets;
        private readonly int _damage;

        public MultipleTargetAttackCommand(IEnumerable<IUnit> targets, int damage)
        {
            _targets = targets;
            _damage = damage;
        }

        public Task Execute(IUnit unit, GridController controller)
        {
            controller.UnitManager.MarkAsAttacking(unit, _targets.First());

            foreach (var target in _targets)
            {
                target.ModifyHealth(-_damage, unit);
            }
            return Task.CompletedTask;
        }

        public Task Undo(IUnit unit, GridController controller)
        {
            // Implementation skipped for brevity
            return Task.CompletedTask;
        }
    }
}

```
#### The CompoundAbility
The `CompoundAbility` allows for the creation of abilities that act as containers for multiple selectable abilities. This can be useful for scenarios like a spellbook or a menu of different attacks, where the player must choose between several abilities.

Here’s a breakdown of how the `CompoundAbility` works:
##### Initializing Abilities
The `CompoundAbility` contains a list of selectable abilities, which are set up during initialization. Each ability is registered with the unit, allowing them to be used during gameplay. This is done by iterating over the `_selectableAbilities` array and calling `RegisterAbility` for each one.
```csharp
public override void Initialize(GridController gridController)
{
    foreach (var ability in _selectableAbilities)
    {
        UnitReference.RegisterAbility(ability, gridController);
    }
}
```
##### Displaying Abilities
When the `CompoundAbility` is selected, it generates a button for each of the selectable abilities. These buttons are added as children to a predefined UI element (e.g., a menu), and each button is linked to one of the abilities. When a button is pressed, the game switches to the selected ability by setting the `GridState` to `GridStateUnitSelected`, passing the corresponding ability.
```csharp
public override void Display(GridController gridController)
{
    foreach (var ability in _selectableAbilities)
    {
        var buttonInstance = GameObject.Instantiate(_buttonTemplate.gameObject, _buttonParent).GetComponent<Button>();
        _buttons.Add(buttonInstance);

        buttonInstance.onClick.AddListener(() =>
        {
            gridController.GridState = new GridStateUnitSelected(UnitReference, ability);
        });

        /*...*/
        // Assign a text or image representing the ability to the button
        /*...*/

        buttonInstance.gameObject.SetActive(true);
    }

    _buttonParent.gameObject.SetActive(true);
}
```
##### Cleaning Up
To clean up after the `CompoundAbility` is deselected or canceled, all generated buttons are removed from the UI element, and the parent is hidden to prevent it from remaining visible.
```csharp
public override void CleanUp(GridController gridController)
    {
        for (int i = 0; i < _buttons.Count; i++)
        {
            GameObject.Destroy(_buttons[i].gameObject);
        }
        _buttons.Clear();
        _buttonParent.gameObject.SetActive(false);
    }
```
##### Full code
```csharp
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.UI;
using System.Threading.Tasks;

public class SpellBookAbility : Ability
{
    [SerializeField] private List<Ability> _selectableAbilities;
    [SerializeField] private GameObject _buttonParent;
    [SerializeField] private Button _buttonTemplate;

    private IList<Button> _buttons = new List<Button>();

    public override void Initialize(GridController gridController)
    {
        foreach (var ability in _selectableAbilities)
        {
            UnitReference.RegisterAbility(ability, gridController);
        }
    }

    public override void Display(GridController gridController)
    {
        foreach (var ability in _selectableAbilities)
        {
            var buttonInstance = GameObject.Instantiate(_buttonTemplate.gameObject, _buttonParent).GetComponent<Button>();
            _buttons.Add(buttonInstance);

            buttonInstance.onClick.AddListener(() =>
            {
                gridController.GridState = new GridStateUnitSelected(UnitReference, ability);
            });

            /*...*/
            // Assign a text or image representing the ability to the button
            /*...*/

            buttonInstance.gameObject.SetActive(true);
        }

        _buttonParent.gameObject.SetActive(true);
    }

    public override void CleanUp(GridController gridController)
    {
        for (int i = 0; i < _buttons.Count; i++)
        {
            GameObject.Destroy(_buttons[i].gameObject);
        }
        _buttons.Clear();
        _buttonParent.gameObject.SetActive(false);
    }
}
```
## 7. AI System
The AI in the Turn-Based Strategy Framework is built on Behaviour Trees, a system that allows for modular, scalable decision-making. Behaviour trees make it easier to define AI behaviours by breaking down decisions into simple, reusable components called nodes. This allows for flexibility in AI logic and makes debugging and extending AI behaviours much simpler.

At the core of the AI system is the AIPlayer class, which controls the units assigned to it during its turn. Each unit controlled by the AI follows a set of decisions defined by its own behaviour tree. By default, the Framework provides a `RegularBehaviourTreeResource`, a general-purpose behaviour tree that handles standard actions like moving and attacking. The AIPlayer handles selecting units, triggering their behaviour trees, and executing actions on the grid.

### AIPlayer and Unit Selection

In the Turn-Based Strategy Framework, the **AIPlayer** class is responsible for controlling units during its turn. AI players are set up automatically by the Grid Helper, or they can be manually added by attaching an **AIPlayer** script to a GameObject under the **PlayersManager** in the scene. During its turn, the AIPlayer selects units, commands them using their behaviour trees, and continues this process until all units have acted.

The order in which the AI controls its units is determined by the **IUnitSelector** interface. The default implementation, **RegularUnitSelector**, selects units in the order provided by the **UnitManager**. In Unity, the **IUnitSelector** is implemented by **UnityUnitSelector**, which can be extended to implement custom selection strategies. For example, units could be prioritized based on health, proximity to enemies, or remaining action points. The unit selector is typically added as a child of the AIPlayer in the scene and assigned to its `_unitSelector` field.

This approach allows flexibility in how the AIPlayer processes its units, enabling developers to create custom behaviors that fit specific game requirements.

### Behaviour Trees and Nodes

In the Turn-Based Strategy Framework, AI actions are driven by **behaviour trees**. A behaviour tree is a modular system that breaks down AI decision-making into smaller, manageable components called **nodes**. Each node represents an action or decision and returns either **true** (success) or **false** (failure), which determines the flow of execution within the tree.

At its core, the behaviour tree relies on the outcome of each node to control how the AI proceeds. If a node succeeds, the AI can move on to the next action or decision. If a node fails, the tree might choose a different path or retry an action. This flexibility allows behaviour trees to handle complex decision-making with relative ease. Nodes are structured hierarchically, meaning higher-level nodes determine which actions to take based on the success or failure of their child nodes.

For example:
- A **SequenceNode** will execute its child nodes in order. If all child nodes succeed, the sequence is considered successful. However, if any child node fails, the sequence stops and returns failure.
- A **SelectorNode** works like an "if-else" statement. It checks its child nodes one by one, returning success as soon as one succeeds. If all child nodes fail, the selector returns failure.

These nodes form the foundation of AI behaviour:
- **SuccederNode**: Forces its child node to return success, even if it would normally fail.
- **InverterNode**: Reverses the result of its child node (turning success into failure and vice versa).
- **DelayNode**: Adds a time delay before the next node is executed, simulating a pause or deliberation in decision-making.
- **RandomNode**: Introduces probabilistic behaviour by returning success or failure based on a specified probability. This node is useful for adding randomness to AI decisions, making AI behaviour less predictable.
- **DebugNode**: Executes a custom action for debugging, such as printing a message or pausing AI for user input.
- **FuncNode**: Executes an arbitrary function, allowing custom logic without needing a dedicated node class. Useful for rapid prototyping.

In addition to these basic nodes, the framework provides **custom nodes** specifically designed for turn-based games:
- **HealthThresholdNode**: Determines whether a unit’s health is above or below a certain threshold, guiding decisions like retreating or attacking.
- **EnemiesInRangeNode**: Checks if there are enemy units within the unit’s attack range, allowing the AI to decide whether to engage or reposition.
- **CellTakenNode**: Determines if a particular cell on the grid is occupied.

#### Action Nodes and Evaluators

In behaviour trees, **action nodes**—also known as **leaf nodes**—are the final nodes that actually perform the actions decided by the tree. They are called leaf nodes because they do not have any child nodes and represent the "end" of a decision-making path. Once the behaviour tree has processed all its decisions through higher-level nodes (such as sequences or selectors), a leaf node executes the action. For executing custom abilities, a dedicated action node should be implemented.

The framework includes built-in action nodes such as:
- **MoveActionNode**: Directs the AI unit to move to a specific cell.
- **AttackActionNode**: Commands the AI unit to perform an attack on an enemy unit.

These action nodes are powered by **evaluators** that help the AI make decisions based on a variety of factors. Evaluators are used to assess potential positions (in the case of movement) or targets (in the case of attacks), assigning a score to each option. These scores help the AI choose the most strategic move or target.

The **IPositionEvaluator** interface is used for evaluating positions on the grid, while the **ITargetEvaluator** interface is used for evaluating units as potential targets. Each evaluator calculates a score based on specific conditions, such as the distance to the target or the damage that could be inflicted.

For example:
- **DamageDealtPositionEvaluator**: Scores a position based on the amount of damage that can be dealt to enemy units from that position.
- **DamageReceivedPositionEvaluator**: Scores a position based on how much damage the AI unit would receive from enemy units if it moved to that cell.
- **DistancePositionEvaluator**: Scores positions based on their distance from the AI unit’s current location.
- **HealthTargetEvaluator**: Scores targets based on their current health, prioritizing weaker enemies.

Evaluators can be combined and weighted to adjust the AI’s behaviour. For instance, a **MoveActionNode** might use a combination of evaluators, giving higher weight to the **DamageDealtPositionEvaluator** to prioritize offensive positioning, while also considering **DamageReceivedPositionEvaluator** to avoid unnecessary risk. Parameters like the weight of each evaluator or thresholds can be fine-tuned to adjust the AI’s aggressiveness, cautiousness, or overall playstyle.

### Sample Behaviour Tree
In this section, we will walk through the process of creating a custom behaviour tree node to execute the FireballAbility, and then integrate this node into a simple behaviour tree for an AI unit. This demonstrates how you can extend the AI system to use custom abilities in strategic decision-making.

#### Creating a `CastFireball` node
First, we need to implement a custom behaviour tree node that will allow the AI to use the FireballAbility. This node will find the best target and execute the ability. 

##### Finding the target 
The node searches for the optimal target by identifying the area where the most enemy units are concentrated. For simplicity, this example uses a basic method for selecting the target, but in a real scenario, a set of evaluators could be used to make a more informed decision.
```csharp
var targetCell = _gridController.CellManager.GetCells()
    .OrderByDescending(cell => _gridController.CellManager.GetCells()
        .Where(n => n.GetDistance(cell) <= _radius)
        .Sum(c => c.CurrentUnits.Count > 0
            ? (c.CurrentUnits[0].PlayerNumber == _unitReference.PlayerNumber ? -1 : 1)
            : 0))
    .FirstOrDefault();
```

##### Handling failure
If no such cell is found, the node returns `false` to indicate that the execution failed.
```csharp
if(targetCell == null)
{
    return Task.FromResult(false);
}
```
##### Executing the ability
Once the best target is selected, the affected units are identified, and the command is executed using `Unit.AIExecuteAbility`. A `TaskCompletionSource` is used to delay the completion of the node until the command has finished executing.
```csharp
var targetUnits = _gridController.CellManager.GetCells().Where(c => c.GetDistance(targetCell) <= _radius).SelectMany(c => c.CurrentUnits);

var tcs = new TaskCompletionSource<bool>();
_unitReference.AIExecuteAbility(new FireballAbility.MultipleTargetAttackCommand(targetUnits, _damage), _gridController, tcs);

return tcs.Task;
```
##### Full code
```csharp
public class CastFireballNode : ITreeNode
{
    private IUnit _unitReference;
    private IGridController _gridController;

    private int _radius;
    private int _damage;

    public CastFireballNode(IUnit unitReference, IGridController gridController, int radius, int damage)
    {
        _unitReference = unitReference;
        _gridController = gridController;
        _radius = radius;
        _damage = damage;
    }

    public Task<bool> Execute()
    {
        var targetCell = _gridController.CellManager.GetCells()
            .OrderByDescending(cell => _gridController.CellManager.GetCells()
                .Where(n => n.GetDistance(cell) <= _radius)
                .Sum(c => c.CurrentUnits.Count > 0
                    ? (c.CurrentUnits[0].PlayerNumber == _unitReference.PlayerNumber ? -1 : 1)
                    : 0))
            .FirstOrDefault(); // Select the area where most enemies are concentrated

        if(targetCell == null)
        {
            return Task.FromResult(false); // Return false to indicate that the node failed to execute.
        }

        var targetUnits = _gridController.CellManager.GetCells().Where(c => c.GetDistance(targetCell) <= _radius).SelectMany(c => c.CurrentUnits);

        var tcs = new TaskCompletionSource<bool>();
        _unitReference.AIExecuteAbility(new FireballAbility.MultipleTargetAttackCommand(targetUnits, _damage), _gridController, tcs);

        return tcs.Task;
    }
}
```

#### Creating custom Behaviour Tree
Creating custom behaviour trees involves extending the `BehaviourTreeResource` class and overriding its `Initialize` method. The implementation should assign the behaviour tree to the `BehaviourTree` property, which is accessed and executed by the AIPlayer during its turn. Let’s break down the implementation of a simple behaviour tree that uses the FireballAbility, moves to a better position, and attacks an enemy if one is within range.

##### The tree root
The `SequenceNode` is used as the root of the tree. The node executes it's child nodes in sequence until one of them fails. In this case, we want the node to execute all it's child nodes.
```csharp
public override void Initialize(IUnit unit, GridController gridController)
{
    BehaviourTree = new SequenceNode(new List<ITreeNode>()
    {
       /*...*/
    });
}
```
##### Casting the Fireball
To cast the Fireball, we use the previously introduced `CastFireballNode`. It is wrapped in a `SuccederNode`, ensuring that the sequence continues even if casting the Fireball fails for some reason (e.g., no valid target).
```csharp
new SuccederNode(
    new CastFireballNode(unit, gridController, radius: 2, damage: 10)
),
```
##### Moving to a position
The `MoveActionNode` is used to move the unit to a more advantageous position. It evaluates potential positions using a set of evaluators to determine the best option. Like the Fireball node, it is wrapped in a `SuccederNode` to ensure the sequence continues regardless of the result.
```csharp
new SuccederNode(
    new MoveActionNode(unit, gridController, new List<IPositionEvaluator>
    {
        new DamageGivenPositionEvaluator(weight: 1, threshold: 20),
        new DamageReceivedPositionEvaluator(weight: -0.8f),
        new DistancePositionEvaluator(weight: -0.1f, threshold: 10),
        new RandomPositionEvaluator(weight: 0.001f)
    })
),
```
##### Attacking enemies
The attack sequence consists of two nodes: first, the `EnemiesInRangeNode` checks whether there are any enemies within attack range. If it succeeds, the `AttackActionNode` is executed, using target evaluators to prioritize the best target. Since this is the final action in the sequence, there’s no need to wrap it in a `SuccederNode`.
```csharp
new SequenceNode(new List<ITreeNode>
{
    new EnemiesInRangeNode(unit, gridController),
    new AttackActionNode(unit, gridController, new List<ITargetEvaluator>
    {
        new HealthTargetEvaluator(1),
        new DamageGivenTargetEvaluator(1)
    })
})
```
##### Full code
```csharp
public class SimpleBehaviourTreeResource : BehaviourTreeResource
{
    public override void Initialize(IUnit unit, GridController gridController)
    {
        BehaviourTree = new SequenceNode(new List<ITreeNode>()
        {
            new SuccederNode(
                new CastFireballNode(unit, gridController, radius: 2, damage: 10)
            ),
            new SuccederNode(
                new MoveActionNode(unit, gridController, new List<IPositionEvaluator>
                {
                    new DamageGivenPositionEvaluator(weight: 1, threshold: 20),
                    new DamageReceivedPositionEvaluator(weight: -0.8f),
                    new DistancePositionEvaluator(weight: -0.1f, threshold: 10),
                    new RandomPositionEvaluator(weight: 0.001f)
                })
            ),
            new SequenceNode(new List<ITreeNode>
            {
                new EnemiesInRangeNode(unit, gridController),
                new AttackActionNode(unit, gridController, new List<ITargetEvaluator>
                {
                    new HealthTargetEvaluator(1),
                    new DamageGivenTargetEvaluator(1)
                })
            })
        });
    }
}
```

## 8. Game State Management
### User Interaction

User interaction with the game is managed by the `GridController` object. The `GridController` listens for various events, such as selecting a unit or cell, and delegates handling these events to a `GridState` object that is assigned to it. The project includes several `GridState` implementations, each designed for specific scenarios:

- **`GridStateAwaitInput`** – The default state when the grid is waiting for player input, specifically for unit selection.
- **`GridStateBlockInput`** – A state where all input is blocked, usually during the AI’s turn.
- **`GridStateUnitSelected`** – The state when a unit is selected by the player, allowing interaction with that unit’s set of abilities.
- **`GridStateGameEnded`** – A state that signals the end of the game, preventing any further interaction or state changes.

To select a specific unit, you can change the grid state to `GridStateUnitSelected` like this:

```csharp
gridController.GridState = new GridStateUnitSelected(unit, unit.GetBaseAbilities());
// Selects the given unit along with its base abilities
```
To deselect the unit and return to the default input state:
```csharp
gridController.GridState = new GridStateAwaitInput();
```
### Turn Management
To properly end a player’s turn, use the `GridController.EndTurn()` method. In Unity, the `UnityGridController` wrapper class also provides this method, which delegates the call to the underlying `GridController`. 

The order in which players take turns is controlled by the `ITurnResolver` interface, which not only defines the turn order but also determines which units are allowed to act during each turn. The framework provides a default implementation, the `SubsequentTurnResolver`, which selects players sequentially, starting with the player who has the lowest player number and cycling through in order.

This default behaviour is useful for many classic turn-based games, but if you need a more advanced system (such as speed-based turns or priority systems), you can create your own resolver by extending the `UnityTurnResolver`. You can easily swap out the resolver by assigning a new one to the `UnityGridController._turnResolver` field in the scene.

Here’s the code for the default `SubsequentTurnResolver`, which is added to the scene by the GridHelper:

```csharp
using System.Linq;

namespace TurnBasedStrategyFramework.Common.Controllers.TurnResolvers
{
    public readonly struct SubsequentTurnResolverImpl : ITurnResolver
    {
        public readonly TurnContext ResolveStart(GridController gridController)
        {
            var nextPlayer = gridController.PlayerManager.GetPlayers().OrderBy(p => p.PlayerNumber).FirstOrDefault();
            var allowedUnits = gridController.UnitManager.GetUnits().Where(u => u.PlayerNumber == nextPlayer.PlayerNumber);
            return new TurnContext(nextPlayer, allowedUnits);
        }

        public readonly TurnContext ResolveTurn(GridController gridController)
        {
            var numberOfPlayers = gridController.PlayerManager.GetPlayers().Count();
            var nextPlayerNumber = (gridController.TurnContext.CurrentPlayer.PlayerNumber + 1) % numberOfPlayers;

            while (!gridController.UnitManager.GetUnits().Where(u => u.PlayerNumber.Equals(nextPlayerNumber)).Any())
            {
                nextPlayerNumber = (nextPlayerNumber + 1) % numberOfPlayers;
            }

            var nextPlayer = gridController.PlayerManager.GetPlayers().FirstOrDefault(p => p.PlayerNumber == nextPlayerNumber);
            var allowedUnits = gridController.UnitManager.GetUnits().Where(u => u.PlayerNumber == nextPlayerNumber);

            return new TurnContext(nextPlayer, allowedUnits);
        }
    }
}
```

### Ending the Game

The system for ending the game in the Turn-Based Strategy Framework is open-ended, meaning there is no built-in mechanism that constantly checks for game-ending conditions. Instead, it's based on a "tell, don't ask" approach, where the game doesn’t automatically monitor for an end condition. In other words, instead of the framework constantly checking game end conditions, you manually inform it when the game ends based on events you subscribe to. It’s up to you to track game progress and manually trigger the end by calling the `GridController.InvokeGameEnded(GameResult gameResult)` method when the conditions are met. There is no specific interface or rule for handling game-ending logic, giving you complete flexibility to implement custom scenarios.

To handle this, you typically follow relevant events in the game (such as unit destruction or objective capture) and subscribe to those events. When a specific condition is met, you invoke the `InvokeGameEnded` method with the appropriate `GameResult`, like declaring a player as the winner. For example, the default implementation added by the GridHelper subscribes to the `unitDestroyed` event for every unit on the grid. It monitors the state of the game and checks if only one player has units remaining. If that’s the case, it calls `InvokeGameEnded`, declaring the last player standing as the winner. Here's the full code for this condition:

```csharp
public class DominationCondition : MonoBehaviour
{
    [SerializeField] private UnityUnitManager _unitManager;
    [SerializeField] private UnityPlayerManager _playerManager;
    [SerializeField] private UnityGridController _controller;

    public override void Awake()
    {
        _unitManager.UnitRemoved += OnUnitRemoved;
    }

    private void OnUnitRemoved(IUnit unit)
    {
        var playersWithUnitsAlive = _unitManager.GetUnits()
                                                .Select(u => u.PlayerNumber)
                                                .Distinct();
        if (playersWithUnitsAlive.Count() == 1)
        {
            var winner = _playerManager.GetPlayers()
                                       .First(p => p.PlayerNumber == playersWithUnitsAlive.First());
            var losers = _playerManager.GetPlayers()
                                       .Where(p => p != winner);

            _controller.InvokeGameEnded(new GameResult(winner, losers));
        }
    }
}
```

For organizational purposes, the default script is placed under a dedicated empty node called `GameEndConditions`, with the script as its child. However, this is not required. You can place the game-ending script anywhere in the scene as long as it can access the necessary events and call the `InvokeGameEnded` method at the right time.

This flexible system allows for a wide variety of game-ending conditions. For example, you could implement a timed match where the game ends after a set number of turns by subscribing to the `UnityGridController.TurnEnded` to count turns. Alternatively, you could create objective-based victory conditions by tracking whether specific position is captured, using the `Unit.UnitEnteredCell` event. For score-based games, you might follow your custom score-counting system and call `InvokeGameEnded` when a player reaches a certain score threshold. This open-ended event-driven approach makes it easy to customize the conditions that end your game.

## 9. Online Multiplayer

The Framework includes online play capabilities, allowing for the integration of multiplayer features into your games. This chapter provides a quickstart guide, outlining the essential steps for incorporating online play. Key aspects include setting up a NetworkConnection, managing server connections, and ensuring consistent game state across all client instances.

### Architecture  
The core of online play is the abstract `NetworkConnection` class. It intercepts all game‑critical actions (e.g. activating an ability, ending a turn), serializes them, broadcasts to other clients, then deserializes and applies them—guaranteeing a consistent game state everywhere. The architecture is peer-to-peer: each client is responsible for broadcasting its own actions and interpreting incoming ones. A central server is still used for user authentication, room discovery, and message relay, but no gameplay logic needs to run on the server. This simplifies hosting, reduces backend complexity, and allows developers to build fully playable online matches without writing authoritative server code. The tradeoff is reduced cheat resistance and less control over enforcement.

Any online play service provider can be used, as long as a custom `NetworkConnection` implementation is provided that integrates with that provider's API.

Key responsibilities of your `NetworkConnection` implementation:  
- **Server Connection**: Establish and manage the socket/session to your game server.  
- **Room Management**: Create, list and join public or private match rooms.  
- **Player Management**: Track players entering/leaving rooms and maintain their metadata.  
- **Match State Communication**: Send/receive all in‑game actions and state changes.  
- **RNG Initialization**: Seed `UnityEngine.Random` the same on all clients for reproducible randomness.  

A complete Nakama‑based example implementation is available on GitHub: [nakama-client](https://github.com/mzetkowski/tbsf-nakama-client)

### Scene Setup  
Follow these steps to set up the scene for online play:
1. **Disable immediate start**  
   - Open your main scene, select the `CellGrid` component and uncheck **ShouldStartGameImmediately**.  
2. **Add the Network GUI**  
   - Drag **Prefabs/NetworkGUI** into your hierarchy.  
3. **Attach your NetworkConnection**  
   - Create an empty GameObject, attach your `NetworkConnection` subclass (eg, `NakamaConnection` from the client package).  
4. **Wire up references**  
   - In the `NetworkGUI` inspector, assign the **GridController**, **NetworkConnection**, and **PlayersParent** fields.  

### Network GUI  
The provided `NetworkGUI` prefab handles:  
- **Server Login**: Enter a username and connect.  
- **Room Creation**: Create a new public or private room.  
- **Room Listing**: Browse and refresh public matches.  
- **Room Joining**: Join an existing match.  
- **Player Readiness**: Select player number and toggle “Ready” state.

### Game State Synchronization
To keep the game state consistent between clients, all actions—such as movement, attacks, other abilities and ending a turn—are serialized, transmitted, deserialized, and then executed. Every `Command` implementing `ICommand` should provide `Serialize` and `Deserialize` methods. Basic commands in the Framework, like `AttackCommand`, already implement these methods. Here is an example:

```csharp
public Dictionary<string, object> Serialize()
{
    return new Dictionary<string, object>
    {
        { SerializationKeys.TargetID, _target.UnitID },
        { SerializationKeys.Damage, _damage },
        { SerializationKeys.ActionCost, _actionCost }
    };
}

public ICommand Deserialize(Dictionary<string, object> actionParams, IGridController gridController)
{
    var target = gridController.UnitManager.GetUnits().First(u =>
        u.UnitID == (int)actionParams[SerializationKeys.TargetID]);

    var damage = (float)actionParams[SerializationKeys.Damage];
    var actionCost = (int)actionParams[SerializationKeys.ActionCost];

    return new AttackCommand(target, damage, actionCost);
}
```
Both command execution and turn-end synchronization are handled automatically by the `NetworkConnection` class, so you don’t need to manually send these events for standard gameplay.

### Additional Actions
For custom events—like map selection, specific match parameters, player readiness, or choosing player numbers—you'll need to register handlers and send state updates manually. A handler is simply a function that runs when a message with a specific opcode is received by the client. You register it using `AddHandler`, passing the action and the opcode. When that message is received, the corresponding handler will be invoked with the provided parameters. Opcodes are  integer constants that uniquely identify message types in your game protocol. Values 0–3 are reserved by the Framework for core game actions. When defining your own opcodes for custom events, start from 4 or higher to avoid collisions with the built-in message types. To broadcast a custom event to other instances, use the `SendMatchState` method with specific OpCode and a dictionary containing event parameters.

Here's how player readiness and selecting a player number are handled in the `NetworkGUI` class:

```csharp
private void Start()
{
    /*...*/
    _networkConnection.AddHandler((actionParams) => OnPlayerNumberChanged(actionParams), (long)OpCode.PlayerNumberChanged);
    _networkConnection.AddHandler((actionParams) => OnPlayerReadyChanged(actionParams), (long)OpCode.IsReadyChanged);
    /*...*/
}

private GameObject CreatePlayerPanel(NetworkUser user, int userIndex, int maxUserCount, string playerNumber, bool isReady)
{
    /* ... UI setup code ... */

    if (user.UserID.Equals(_localUser.UserID))
    {
        /*...*/
        playerSelectionPanelInstance.transform.Find("PlayerNumber").GetComponent<InputField>().onValueChanged.AddListener((value) =>
        {
            var actionParams = new Dictionary<string, object>
            {
                { "user_id", _localUser.UserID },
                { "player_number", value.ToString() }
            };
            _networkConnection.SendMatchState((long)OpCode.PlayerNumberChanged, actionParams);
        });
    }

    /*...*/

    if (user.UserID.Equals(_localUser.UserID))
    {
        playerSelectionPanelInstance.transform.Find("IsReady").GetComponent<Toggle>().onValueChanged.AddListener((value) =>
        {
            var actionParams = new Dictionary<string, object>
            {
                { "user_id", _localUser.UserID },
                { "is_ready", value.ToString() }
            };
            _networkConnection.SendMatchState((long)OpCode.IsReadyChanged, actionParams);
        });
    }

    /*...*/
}
```
### Nakama Integration
Nakama by Heroic Labs is an open-source server for realtime multiplayer games. A custom Nakama client and server is implemented for the Turn Based Strategy Framework. For legal reasons, these are not included with the project, but available on GitHub instead.

- **Server**: Clone and run the custom Nakama server at `github.com/mzetkowski/tbsf-nakama-server`.
- **Client**: Install the Unity package from `github.com/mzetkowski/tbsf-nakama-client`.
- **Disclaimer**: This project is not endorsed by or affiliated with Heroic Labs. "Nakama" is a trademark of Heroic Labs and is used here for descriptive purposes only. This project's use of the "Nakama" name is not intended to imply any affiliation with or endorsement by Heroic Labs.

## 10. Tutorial
This tutorial will guide you through creating a basic scene using the Turn-Based Strategy Framework, focusing on assembling the necessary components without writing any code. Using tools provided in the framework, such as the **GridHelper**, you will set up a square-based map, add obstacles, and place two human players, each controlling a few units. This hands-on approach is designed to give you practical experience with the framework’s features, allowing you to see the mechanics in action and understand how the various elements work together. By the end, you will have a fully playable scene. The completed tutorial can be found in the `Assets/Examples/tutorial` folder.

### Cell Template

Before generating our map, we need to create its fundamental building block: a single, reusable cell. This **cell prefab** will define the appearance and basic behaviour of every square on our grid. To create a basic square cell, follow the steps outlined below. This guide walks you through setting up the cell structure, adding visual components, and configuring interaction using the `Square.cs` script.

#### 1. Create a New Scene
- In Unity Editor, create and open a new scene by clicking on **File > New Scene**.

#### 2. Create a Cube
- Select **GameObject > 3D > Cube** to create a new cube
- Take note that the created cube includes a collider, a mesh and a material

#### 3. Add a Square.cs script to the cube
- Attach the `Square.cs` to the cube. You can find it in `Assets/Scripts/cells/` folder

#### 4. Set Up Visual Highlighters
To provide visual feedback (such as highlighting cells for selection), we will set up highlighters. These nodes modify the color of the cell in different game states (e.g., selected, reachable, or path).

* Add an empty child **GameObject** to the cube and name it **Highlighters**. This node will group the different highlight states.
    * Right-click on the cube **GameObject** and select **Create Empty**, then rename the new object to `Highlighters`.

* For each state (**UnMark**, **MarkAsHighlighted**, **MarkAsReachable**, and **MarkAsPath**), add an empty **GameObject** as a child of **Highlighters**, attach the `RendererHighlighter.cs` script, and configure the color:

* **UnMark**:
   * Create an empty **GameObject** named "UnMark" as a child of `Highlighters`.
   * Attach the `RendererHighlighter.cs` script to it.
   * On the `RendererHighlighter` component, set `_color` to white.
   * Drag the `Cube` GameObject into the `_renderer` field.

> **Tip:** Copy the **UnMark** GameObject 3 times and adjust the parameters as below. This saves time and reduces repetitive setup by duplicating the GameObject with its attached script and assigned renderer.

* **MarkAsHighlighted**:
   * Create an empty **GameObject** named "MarkAsHighlighted" as a child of `Highlighters`.
   * Attach the `RendererHighlighter.cs` script to it.
   * On the `RendererHighlighter` component, set `_color` to blue.
   * Drag the `Cube` GameObject into the `_renderer` field.

* **MarkAsReachable**:
   * Create an empty **GameObject** named "MarkAsReachable" as a child of `Highlighters`.
   * Attach the `RendererHighlighter.cs` script to it.
   * On the `RendererHighlighter` component, set `_color` to yellow.
   * Drag the `Cube` GameObject into the `_renderer` field.

* **MarkAsPath**:
   * Create an empty **GameObject** named "MarkAsPath" as a child of `Highlighters`.
   * Attach the `RendererHighlighter.cs` script to it.
   * On the `RendererHighlighter` component, set `_color` to green.
   * Drag the `Cube` GameObject into the `_renderer` field.

#### 5. Assign Highlighters to the Square Script

Now that you have set up the highlighters, assign them to the corresponding fields in the `Square.cs` script to ensure that visual feedback works correctly during gameplay.

1. Select the cube GameObject.
2. In the **Inspector**, locate the fields `_unMarkFn`, `_markAsHighlighted`, `_markAsReachableFn`, and `_markAsPathFn` from the attached `Square.cs` script.
3. Assign the correct highlighter GameObjects to these fields:
    - Assign the **UnMark** GameObject to the `_unMarkFn` field.
    - Assign the **MarkAsHighlighted** GameObject to the `_markAsHighlighted` field.
    - Assign the **MarkAsReachable** GameObject to the `_markAsReachableFn` field.
    - Assign the **MarkAsPath** GameObject to the `_markAsPathFn` field.

After completing this step, your cell will be fully functional, providing visual feedback based on the player's interaction and responding to different game states.

#### 6. Save the cell prefab
- Drag the cube from the Hierarchy panel into the Project panel to save it as a prefab.

### Generating the Grid Using the Grid Helper

Now that the basic cell template is ready, it's time to generate the grid for your scene. The Turn-Based Strategy Framework includes a handy tool called **GridHelper** that automates grid creation, allowing you to quickly generate a grid using the cell template you just created.

#### 7. **Access the Grid Helper panel**:
- Select **Window > Grid Helper** to acess the Grid Helper panel.

#### 8. **Configure Grid Parameters**:
- In the **GridHelper** panel, configure the following settings to match the scene setup:
   - **Human Players No**: Set this to `2` to include two human players.
   - **AI Players No**: Leave this at `0` since the tutorial focuses on human players only.
   - **Is 2D Map**: Leave this unchecked as the map is 3D-based.
   - **Cell Prefab**: Drag and drop the cell prefab you created earlier into this field.
   - **Map Width and Height**: Set both the **Map Width** and **Map Height** to `10` to generate a 10x10 grid.

#### 10. **Generate the Grid**:
- Once all parameters are set, click the **Generate Scene** button. The GridHelper will automatically generate a 10x10 grid, with each cell based on the square cell template you've provided.

By following these steps, you will have a functional, grid-based map with two human players, ready for gameplay interactions.

### Creating an Obstacle Cell

To add variety to the map and create impassable areas, we’ll create a modified version of the basic square cell with a "rock" on top, which will serve as an obstacle. This obstacle cell inherits from the previous square cell you created, maintaining the core grid functionality while adding an additional mesh to represent the rock.

#### 10. **Create a prefab variant**:
- Navigate to the cell prefab created before, right-click on it and select **Create > Prefab Variant**.
- Double-click the new prefab to open it for editing.

#### 11. **Add the Rock Mesh**:
- Right-click on the root Game Object in the prefab and select **Create > 3D > Cube**
- With the new **Cube** selected, go to the Inspector panel and:
   - Under **Transform**, adjust **Scale** to `(0.75, 0.75, 0.75)` and **Translation** to `(0, 0.75, 0)` to place it slightly raised above the cell.
   - Right-click in the Project panel and select **Create > Material** to create a new material. Assign the new material to the `Material` field on the Mesh Renderer component.
   - Adjust the **Albedo** property of the new material to black to differentiate it visually as a rock.

#### 12. **Mark the Obstacle Cell as Occupied**:
- Since this cell has a rock on it and should act as an obstacle, make sure to set the **`isTaken`** property in the `Square.cs` script to `true`.

#### 13. **Save the Obstacle Cell Prefab**:
- Save the prefab to keep the obstacle cell’s setup intact. The cell is now ready to act as an obstacle on your map.

With this setup, the obstacle cell can now be used as a tile type in the map. Next, we’ll use the **Tile Painter** tool to place these obstacles on the map.

### Painting Obstacles onto the Grid

#### 14. **Open the Tile Painter**:
- With the generated grid scene open, go to the **GridHelper** panel.
- Find the **Tile Painter** section, where you’ll be able to select and apply different cell types to specific parts of the grid.

#### 15. **Select the Obstacle Cell**:
- In the **Tile Painter** options, set the **Tile Prefab** to the obstacle cell prefab you just created.

#### 16. **Enter Tile Edit Mode**:
- Click **Enter Tile Edit Mode** to enable painting on the grid. Now, any cell you click on will be replaced by the selected obstacle cell.

#### 17. **Paint the Obstacles**:
- Click on cells across the grid to replace them with the obstacle tile.

#### 18. **Exit Tile Edit Mode**:
- When you’re done, click **Exit Tile Edit Mode** to return to the standard scene editing view.

By following these steps, you’ve added obstacles to your map, enhancing its strategic layout with simple, flexible tools.

### Creating the Unit Template

To set up a unit template in Unity, we’ll create a new unit prefab with visual elements, collision detection, and interactive capabilities. This unit template will serve as the base for all player-controlled and AI units on the battlefield. Let’s walk through the steps to build this unit template from scratch.

#### 19. **Create an Empty Game Object**:
- Start by creating an empty **GameObject**: click on **GameObject > Create Empty**. Rename it `Unit`. This `Unit` GameObject will be the root of your unit prefab.

#### 20. **Attach the Unit Script**:
- With the `Unit` GameObject selected in the **Hierarchy**, click **Add Component** in the **Inspector**. Search for and select the `Unit.cs` script. You'll typically find it in `Assets/Scripts/units/`.

#### 21. **Add the Unit’s 3D model**:
- To represent the unit visually, add a **Cube** as a child of the `Unit` GameObject.
   - Right-click on the `Unit` GameObject in the Hierarchy and select **3D Object > Cube**. Rename this new Cube `UnitMesh`.
- Adjust the **Transform** properties of `UnitMesh` in the **Inspector**:
   - Set **Scale** to `(0.75, 0.75, 0.75)` to resize the cube.
   - Set **Position** to `(0, 1.25, 0)` to place the cube slightly elevated from the ground.

#### 22. **Add an Additional Mesh for Highlighting**:
- Create a second **Cube** as a child of the root `Unit` GameObject. This mesh will provide a visual highlight effect for the unit.
   - Right-click on the `Unit` GameObject in the Hierarchy and select **3D Object > Cube**.
   - Rename it `HighlightMesh`.
- Adjust the **Transform** properties of `HighlightMesh` in the **Inspector**:
   - Set **Scale** to `(1.2, 0.1, 1.2)` to make it a flat, broad shape that extends slightly beyond the base of the unit.
   - Set **Position** to `(0, 0.5, 0)` to place it just beneath the main unit mesh, creating a visible highlight around the base of the unit.

#### 23. **Set Up Highlighters for Visual Feedback**:
- To handle different visual states (e.g., selected, friendly, finished), add a new **GameObject** as a child of the `Unit` GameObject and name it **Highlighters**.
   - Right-click on the `Unit` GameObject in the Hierarchy and select **Create Empty**. Rename it `Highlighters`.

- Add child **GameObjects** under **Highlighters** to represent each visual state. Attach the `RendererHighlighter.cs` script to each of these new GameObjects, then configure their properties:

* **UnMark**:  
   - Create an empty **GameObject** named "UnMark" as a child of `Highlighters`.
   - Attach the `RendererHighlighter.cs` script to it.
   - On the `RendererHighlighter` component, set `_color` to white.
   - Drag the `HighlightMesh` GameObject into the `_renderer` field.

> Tip: Copy the UnMark GameObject 4 times and adjust the parameters as below. This saves time and reduces repetitive setup by duplicating the GameObject with its attached script and assigned renderer.

* **MarkAsSelected**:  
   - Create an empty **GameObject** named "MarkAsSelected" as a child of `Highlighters`.
   - Attach `RendererHighlighter.cs`.
   - Set `_color` to blue.
   - Assign the `HighlightMesh` to the `_renderer` field.

* **MarkAsFriendly**:  
   - Create an empty **GameObject** named "MarkAsFriendly" as a child of `Highlighters`.
   - Attach `RendererHighlighter.cs`.
   - Set `_color` to green.
   - Assign the `HighlightMesh` to the `_renderer` field.

* **MarkAsFinished**:  
   - Create an empty **GameObject** named "MarkAsFinished" as a child of `Highlighters`.
   - Attach `RendererHighlighter.cs`.
   - Set `_color` to gray.
   - Assign the `HighlightMesh` to the `_renderer` field.

* **MarkAsTargetable**:  
   - Create an empty **GameObject** named "MarkAsTargetable" as a child of `Highlighters`.
   - Attach `RendererHighlighter.cs`.
   - Set `_color` to red.
   - Assign the `HighlightMesh` to the `_renderer` field.

* **MarkAsAttacking / MarkAsDefending**:  
   - Create an empty **GameObject** named "MarkAsAttacking" as a child of `Highlighters`. Attach `SwayHighlighter.cs` to it.
   - Create an empty **GameObject** named "MarkAsDefending" as a child of `Highlighters`. Attach `SwayHighlighter.cs` to it.

#### 24. **Configure SwayHighlighter Parameters for MarkAsAttacking and MarkAsDefending**:
The **SwayHighlighter** provides a dynamic swaying effect, perfect for visually signaling a unit's aggressive or defensive state. Adjust the following parameters on the objects created in the previous step:

- **_magnitude**: This controls the intensity of the sway, or how much the unit "leans" or "bobs" during the animation. Higher values will produce a more pronounced effect.
   - For **MarkAsAttacking**: Set `_magnitude` to `0.5` for a noticeable sway when the unit is preparing to attack, giving a sense of forward motion.
   - For **MarkAsDefending**: Set `_magnitude` to `-0.25`, creating a more subtle, backward lean that suggests a defensive stance.

- **_swayCurve**: This parameter defines the swaying motion over time, represented by a **Curve** resource.
- Click on the **Curve** field in the Inspector, which opens a curve editor where you can control the sway's timing and smoothness.
- The sample curve includes three key points:
   - `Vector2(0, 0)`: The starting point, which defines the initial position.
   - `Vector2(0.5, 1)`: The peak of the sway at halfway, creating the maximum "lean."
   - `Vector2(1, 0)`: Returns the unit to its starting position at the end of the cycle.
- This curve can be adjusted as needed to make the sway faster, slower, or more dramatic by manipulating the height and position of these points.

- **_targetTransform**: This field references the part of the unit affected by the sway. Set `_targetTransform` to the root `GameObject` so the sway applies to the entire unit.

#### 25. **Assign Highlighters to Fields in Unit Script**

With the highlighters set up, you’ll now assign each to the corresponding field in the `Unit.cs` script.

* Select the root unit GameObject, and in the Inspector, locate the properties for each highlighter under the `Unit.cs` script.
* Assign the highlighter nodes to their respective fields:
   - **_unMarkFn**: Set to `Highlighters/UnMark`.
   - **_markAsSelectedFn**: Set to `Highlighters/MarkAsSelected`.
   - **_markAsFriendlyFn**: Set to `Highlighters/MarkAsFriendly`.
   - **_markAsFinishedFn**: Set to `Highlighters/MarkAsFinished`.
   - **_markAsTargetableFn**: Set to `Highlighters/MarkAsTargetable`.
   - **_markAsAttackingFn**: Set to `Highlighters/MarkAsAttacking`.
   - **_markAsDefendingFn**: Set to `Highlighters/MarkAsDefending`.

#### 26. **Automatic Configuration of Abilities and Brain**

When you attach the `Unit` script to a GameObject, it automatically adds two basic abilities—`MoveAbility` and `AttackAbility`—to streamline the setup process. These default components provide core functionality for movement and combat.

- You may remove or replace these abilities later, but for the purposes of this tutorial, leave them as they are.

Additionally, a default `BehaviourTreeResource` is assigned to the unit’s `Brain` object to provide basic AI behaviour.

- This behaviour tree can be customized as needed, but no changes are required for this tutorial.

#### 27. **Save the Unit Template**:
- Save this unit prefab as the base template for units in the game. Drag the unit GameObject from the Hierarchy panel into the Project panel.

#### 28. **Create Color Variations for Each Player**:
- To differentiate units for each player, create a **new prefab variant** from this base unit template for each player.
-    Right-click on the unit prefab in the Project panel and select **Create > Prefab Variant**
- Create two new materials for each player
   - Right-click in the Project panel and select **Create > Material**
   - Modify the **Albedo** property on each new material to a unique color (e.g., blue for Player 1 and red for Player 2).
- Assign the new materials to the **UnitMesh** of each prefab.
- Save each player’s unit prefab, and you’re ready to add these units to the game map.

#### 29. **Adding Units to the Game Using the Unit Painter**

With the unit templates ready, you’ll use the **Unit Painter** feature in **GridHelper** to place the units on the map, allowing you to set up each player's units.

* **Open the Unit Painter**:
   - In the Unity Editor, navigate to the **GridHelper** panel.
   - Find the **Unit Painter** section within the panel.

* **Select a Unit Prefab**:
   - In the **Unit Painter** panel, set the **Unit Prefab** field by selecting one of the player-specific unit prefabs you created earlier (e.g., the blue unit for the first player).

* **Assign Player Number**:
   - Set the **Player Number** field to match the player for whom you are placing units. For example, set it to `0` for the first player and `1` for the second player.

* **Enter Unit Edit Mode**:
   - Click **Enter Unit Edit Mode**. This enables placement mode on the grid, allowing you to place units by clicking on cells.

* **Place Units on the Map**:
   - Click on the cells where you want to place the units for the selected player. Place a few units for each player in different locations to set up the initial scene for gameplay.

* **Exit Unit Edit Mode**:
   - Once you’ve placed all desired units, click **Exit Unit Edit Mode** to finalize the setup and return to the standard editor view.

### Completing the Tutorial

With the units placed, your turn-based strategy scene is now fully configured and ready for testing. You have set up a square-based grid, added obstacles, and placed two human players with units, all without writing any code. This provides a practical foundation for exploring the Turn-Based Strategy Framework further, including options for additional features or customization.

Your scene is now ready to play and test. Open the scene in the Unity Editor, press **Play**, and observe the framework in action.

## 11. Beyond the Basics: Pushing the Limits of the Turn-Based Strategy Framework
The previous chapters covered the core features and workflows, but the Framework offers far more for experienced developers willing to explore its full potential. This chapter is an open-ended collection of advanced use cases, that go beyond Turn-Based Strategy Framework basics.

### 1. Using Unity Tilemap System for maps

In the basic setup, a map in the Framework consists of individual GameObjects, each representing a cell. This approach is intuitive—it’s easy to inspect, debug, and directly manipulate each cell in the editor. However, it doesn't scale well. Once you exceed a few hundred cells, performance becomes an issue.

But a cell doesn't need to be a GameObject. It can be a lightweight C# class that implements the ICell interface, without any presence in the Unity scene hierarchy. When combined with a custom ICellManager implementation, this allows you to manage the grid purely in memory—drastically reducing overhead and enabling much larger maps.

In the scene, such maps can be represented in different ways: as pre-made meshes, procedurally generated geometry, images, or—most effectively—using Unity’s Tilemap system. The Framework includes a demo using the Tilemap; you can find it in the `Examples/TilemapExample` folder and here's a short recap of how it's done:

* The Tilemap consists of two layers: a visual layer, where the map is drawn, and a data layer, where gameplay data (e.g. movement cost) is encoded.
* Instead of cell prefabs, the data layer is painted using DataTile tiles that store gameplay-related properties:
```csharp
public class DataTile : Tile
{
    public int movementCost = 1;
    public bool isWalkable = true;
    public ScriptableObject cellType;
}
```
* A custom `TilemapCellManager` replaces the default `RegularCellManager` in the scene. It reads from the data layer and builds the in-memory grid:
```csharp
public override void Initialize(IGridController gridController)
{
    BoundsInt bounds = _tilemap.cellBounds;
    _cells = new Dictionary<IVector2Int, VirtualSquareCell>();

    foreach (Vector3Int pos in bounds.allPositionsWithin)
    {
        DataTile tile = _tilemap.GetTile<DataTile>(pos);
        if (tile == null)
        {
            continue;
        }
        var worldPosition = _tilemap.GetCellCenterWorld(pos).ToIVector3();
        var gridPosition = new Vector2IntImpl(pos.x, pos.y);
        var cell = new VirtualSquareCell(gridPosition, worldPosition, tile.movementCost, false, tile.cellType);
        _cells.Add(gridPosition, cell);
        CellAdded?.Invoke(cell);
    }
    _selectedCell = _cells.Values.First();
}
```
### 2. Porting to other engines
The core of the Framework's code is written in a way that's decoupled from any specific engine dependencies. This makes it easy to port your gameplay to different game engine that uses C# for scripting. To facilitate the transition, I would advice to structure your code in the folowing way: whenever possible, make your mechanics engine-agnostic. Then, reference this implementation in engine-specific code. This is how `AttackAbility` and `MoveAbility` are implemented in the Framework:
* The underlying logic is implemented in common `AttackAbilityImpl` class:
```csharp
public class AttackAbilityImpl : IAbility
{
    public void OnAbilitySelected(IGridController gridController)
    {
        var enemyUnits = gridController.UnitManager.GetEnemyUnits(gridController.TurnContext.CurrentPlayer);
        _attackableUnits = new HashSet<IUnit>(enemyUnits.Where(u => UnitReference.IsUnitAttackable(u, u.CurrentCell, UnitReference.CurrentCell)));
    }

    public async void Display(IGridController gridController)
    {
        await gridController.UnitManager.MarkAsTargetable(_attackableUnits);
    }

    public void CleanUp(IGridController gridController)
    {
        gridController.UnitManager.UnMark(_attackableUnits);
    }

    // The rest of the methods skipped for brevity
```

* Then, the actual Unity implementation references this code like this:
```csharp
public class AttackAbility : Ability
{
    private AttackAbilityImpl _attackAbility;
    public override void Initialize(IGridController gridController)
    {
        base.Initialize(gridController);
        _attackAbility = new AttackAbilityImpl(UnitReference);
        _attackAbility.Initialize(gridController);
    }

    public override void Display(IGridController gridController)
    {
        _attackAbility.Display(gridController);
    }

    public override void CleanUp(IGridController gridController)
    {
        _attackAbility.CleanUp(gridController);
    }

    public override void OnAbilitySelected(IGridController gridController)
    {
        _attackAbility.OnAbilitySelected(gridController);
    }

    // The rest of the methods skipped for brevity
```
By structuring your code in this way you can make your codebase futureproof and greaty simplify the porting process.

**More ideas to come!**

## 12. Support

Thanks for choosing the Turn-Based Strategy Framework! If you have any questions, need help setting things up, or just want to chat about what you're building, I’d love to hear from you. There are a couple of ways to reach out, so pick what works best for you. You can always email me directly at crookedhead@outlook.com, or, if you prefer live conversations, join the community on Discord at https://discord.com/invite/uBJNPJHFjB. The Discord server is a great place to get quick answers, see what others are creating, and maybe even find some inspiration. I do my best to respond quickly throughout the week. Looking forward to helping you bring your game to life!
