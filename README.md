# Tile Swap Puzzle Game

A mobile puzzle game where players rearrange shuffled image tiles to complete puzzles across multiple levels.

## Features

- **Multiple Grid Sizes**: Play with 3x3, 4x4, and 5x5 puzzle grids with increasing difficulty
- **Level Progression System**: Unlock new levels as you complete challenges
- **Multiple Image Categories**: Nature, Animals, and City-themed puzzles
- **Smooth Animations**: Polished tile movement with visual feedback
- **Mobile Optimized**: Designed for Android and iOS touch controls
- **AdMob Integration**: Banner, interstitial, and rewarded ads for monetization
- **Progress Tracking**: Track your moves, completion times, and maintain best scores
- **Data Persistence**: Save progress across game sessions
- **Interactive Rewards**: Earn hints and smart shuffles through rewarded ads
- **Compatibility**: Designed to work with Unity 2022.3.60f1 with graceful degradation for missing packages

## Project Structure

- **Assets/Scripts**: C# scripts for game functionality
  - GameManager.cs - Core game controller
  - TileGrid.cs - Puzzle grid management and solving
  - Tile.cs - Individual tile behavior
  - UIManager.cs - UI elements and screens
  - AdManager.cs - Ad platform integration (Unity Ads/AdMob)
  - LevelManager.cs - Level loading and progression
  - AudioManager.cs - Sound effects and music
  - SaveManager.cs - Game state persistence
  - PreprocessorDefines.cs - Compatibility directives documentation
  
- **Assets/Scenes**: Unity scene files
  - MainMenu.unity - Game start menu
  - Game.unity - Main gameplay scene

- **Assets/Resources**: Game assets
  - LevelImages/ - Puzzle images sorted by categories
  - Audio/ - Sound effects and music tracks
  - UI/ - UI elements and icons

- **Assets/Prefabs**: Reusable game objects
  - Tile.prefab - Template for puzzle tiles
  - UI/ - UI prefabs for different screen elements

## Getting Started

> **IMPORTANT NOTE:** This project requires Unity to be installed and cannot be run in environments without the Unity Editor. The scripts have been prepared with proper preprocessor directives to ensure compatibility with Unity 2022.3.60f1.

### Prerequisites
- Unity 2021.3 or newer (compatible with Unity 2022.3.60f1+)
- Android SDK/iOS Development Tools for building to mobile

### Optional Packages
The project supports both configurations with and without the following packages:
- **TextMeshPro** - For enhanced text rendering
- **DOTween** - For smooth animations and transitions

### Package Compatibility
To enable enhanced features with optional packages:
1. Install TextMeshPro and/or DOTween from the Package Manager
2. Open Project Settings > Player > Scripting Define Symbols
3. Add the following symbols as needed:
   - `USE_TEXTMESHPRO` - To enable TextMeshPro features
   - `USE_DOTWEEN` - To enable DOTween animations
   - `USE_UI` - To enable enhanced UI features

The project includes fallback implementations when these packages are not available, ensuring core functionality works in all configurations.

### Testing in the Unity Editor
1. Open the project in Unity
2. Open the MainMenu scene in `Assets/Scenes`
3. Press Play to test the game in the editor
4. Use mouse clicks to simulate touch/tap inputs
5. Test different grid sizes and ensure transitions between levels work

### Troubleshooting Compilation Errors
If you encounter compilation errors about missing references:
1. Make sure you've installed the required packages (Unity UI module is essential)
2. For optional packages (TextMeshPro, DOTween):
   - Either install the package from Package Manager
   - Or continue without them (fallbacks are implemented)
3. Check the scripting define symbols in Project Settings > Player:
   - Always include: `USE_UI`
   - Add others as needed based on installed packages

### Building the Project
1. Open the project in Unity
2. Configure your AdMob IDs in AdManager
3. Build for your target platform (Android/iOS)
4. For mobile builds, ensure you have the appropriate build tools installed:
   - Android: Android SDK, JDK
   - iOS: Xcode, macOS

## Game Mechanics

1. **Tile Movement**: Click or tap on a tile adjacent to the empty space to move it
2. **Level Completion**: Complete the puzzle by arranging all tiles in the correct order
3. **Progression**: Complete levels to unlock more challenging puzzles with larger grids

## Customizing Puzzle Images

To add your own custom puzzle images:

1. Place your image files in the `Assets/Resources/LevelImages` folder
2. Images should be:
   - Square format (1:1 aspect ratio) for best results
   - Recommended size: 1024x1024 pixels (or at least 512x512)
   - Supported formats: .png, .jpg
3. Images will automatically be included in the rotation of available puzzles

## Ad Integration

The game is set up to work with both Unity Ads and Google AdMob:

1. For Unity Ads:
   - Enable the UNITY_ADS scripting define symbol
   - Configure your app IDs in AdManager.cs

2. For Google AdMob:
   - Enable the UNITY_ADMOB scripting define symbol
   - Replace the placeholder IDs in AdManager.cs with your own AdMob IDs
   - Banner ads appear at the bottom of the screen
   - Interstitial ads show between levels (with configurable frequency)
   - Rewarded ads are available for hints and additional shuffles

## Performance Optimization

This game has been optimized for mobile platforms with these techniques:

1. **Object Pooling**: Tiles are cached and reused to minimize garbage collection
2. **Memory Management**: 
   - Images are loaded on-demand and unloaded when not needed
   - Sprites are efficiently sliced from source textures 
3. **Rendering Optimizations**:
   - Minimal overdraw
   - Simplified materials
   - Batched UI elements
4. **Battery Considerations**:
   - Reduced update calls when game is idle
   - Efficient coroutine usage
   - Animations paused when app loses focus

## Future Enhancements
- Custom puzzle image import from camera or gallery
- Online leaderboards
- Daily challenges
- Additional puzzle types