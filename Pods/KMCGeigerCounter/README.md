# KMCGeigerCounter

KMCGeigerCounter is a framerate meter that clicks like a Geiger counter when your animation drops a frame.

A Geiger counter detects invisible radiation particles and alerts you to what you can't see. Dropped frames aren't invisible, but it can be hard to tell the difference between 55 and 60 fps. KMCGeigerCounter makes those five dropped frames obvious.

- If you're not consistently animating smoothly, you'll hear a rough, staticky noise.
- If your app runs at a smooth 60 fps, you'll hear the occasional drops to 59 and 58.
- You can even hear dropped frames from CPU spikes, like when custom table view cells enter the screen and require layout.

The onscreen framerate meter shows two numbers:

- The number of frames dropped in the past second
- The number of frames drawn in the past second

The meter is orange when you've dropped at least three frames in the past second.

## Installation

`pod 'KMCGeigerCounter'`

Or copy KMCGeigerCounter.h, KMCGeigerCounter.m, and KMCGeigerCounterTick.aiff into your project.

## Usage

In your `UIApplicationDelegate`, enable the tool:

    - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
    {
        // …
        [self.window makeKeyAndVisible];

        [KMCGeigerCounter sharedGeigerCounter].enabled = YES;
    }

Then, build and run your app. Navigate through your app and listen for clicks.

## Doesn't adding a view to my app reduce the framerate?

Barely. If this causes frames to drop, the app's performance was probably toeing the line too closely in the first place.

## Dumb things you probably thought of, but seriously

Remember to turn off Silent mode, or you won't hear anything. 

You should remove KMCGeigerCounter before shipping to the App Store. It can't be good for battery life.
