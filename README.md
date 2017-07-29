## Adaptive Icons in Android O

### So you want to know about adaptive icons in android O?

Your in luck. This repo will give you a tutorial on how to do it and show you a functioning app with adaptive icons.

Now there is two options to doing adaptive icons

## THE EASY METHOD

First thing your gonna wanna do is open Android Studio 3.0 and create a new project targeted at api 26

If this is not the project you are going to use the adaptive icons for you aare gonna wanna make sure your project is also targeted at api 26

Right click the res folder in adroid studio

Hover over new and select image asset

In the forground tab select the image you want

In the background tab select the color you'd like. (doing an image here would look horrible)

Make sure the preview looks like you want it to.

Select next and click finish

### Now lets clean up a few things

Open values/ic_launcher_background.xml

Copy the color from here and move it to colors.xml (icons are themable in o)

delete ic_launcher_background.xml

If you do not want to support older versions than android o, Delete ic_launcher.png & ic_launcher_round.png in each mipmap folder

### Transfering to our old project

First we need to edit our AndroidManifest.xml
- Set the Target SDK to 26
- Set android:icon to mipmap/ic_launcher
- Set android:roundIcon to @drawable/ic_launcher_round

Now that we have that, we can finish this up by transfering the rest of our files

Move the mipmap folders over to the old project

add this to colors
```bash
<color name="ic_launcher_background"></color>
```

And everthing should be good to go!

## THE HARD WAY

First we need to edit our AndroidManifest.xml
- Set the Target SDK to 26
- Set android:icon to mipmap/ic_launcher
- Set android:roundIcon to @drawable/ic_launcher_round

Now open the res folder and create a few new folders
- mipmap-anydpi-v26
- mipmap-hdpi
- mipmap-mdpi
- mipmap -xhdpi
- mipmap -xxhdpi
- mipmap -xxxhdpi

In mipmap-anydpi-v26 create 2 xmls
- ic_launcher.xml
- ic_launcher_round.xml

both files will look identical

```bash
<?xml version="1.0" encoding="utf-8"?>
<adaptive-icon xmlns:android="http://schemas.android.com/apk/res/android">
    <background android:drawable="@color/ic_launcher_background"/>
    <foreground android:drawable="@mipmap/ic_launcher_foreground"/>
</adaptive-icon>
```

in every other folder you will need 3 icons

these icons can be pngs or xmls

ic_launcher_forground is the name of the forgound image

ic_launcher is the icon for older versions of android

ic_launcher_round is the icon for older pixels

after that add
```bash
<color name="ic_launcher_background"></color>
```
to colors

should be all good to go :)