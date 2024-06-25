# CatDog Design System 
**Make the design your own**

CatDog DS is not a framework or a library. There is no packages to install and no dependancies. The goal is to give you the building blocks for the design system so you can start using it and not just own it but make it your own. 

# Prerequisites

This work for svelte so you need to first create a svelte app. Use the following command.

```bash
npm create svelte@latest myapp
cd myapp
npm install
npm run dev
```

CatDog DS is not affliated with bits-ui but it built on top of it so you need to install it first. Documentation for bits-ui at [`bits-ui-documentaion`](https://www.bits-ui.com/docs/introduction).

To install bits-ui use the following command.

```bash
# install bits-ui
npm install bits-ui

# create a new project in my-app
npm create svelte@latest my-app
```

# Design Style Heirarchy
All the design files are placed in the style folder. If you change the location, make sure to change the imports in the files.

![design-system-heirarchy](https://github.com/alekois/catdogui/assets/92536005/fe82d8b7-db8f-41cb-b13e-1e8adbc81738)

## app.scss
The file just contains all the imports from other scss files. You will just need to import app.scss in any svelte file for you to start using the styles.

## themes.scss
themes.scss contains all the base constants. Brand colors, Baseline sizes and Font family. If you don't want more finer control, just changing the values on this file should have an effect globally. 

The variables in this file are NOT meant to be used when using the design system.

```css
//font
$theme__font-family--primary: "Source Code Pro", monospace;
$theme__font-family--secondary: "Merriweather", serif; 

//size
$baseline__radius: 12px;
$baseline__gap: 1rem; 
$baseline__font-size: 1rem; 
$baseline__asset-size: 1.25rem; 
$baseline__padding: 0.75rem; 
$baseline__border-size: 1px;
$baseline__line-height: 1.5;
$baseline__font-weight: 500;

//colors
$theme__color--primary: #fa7317;
$theme__color--secondary: #7317fa;
$theme__color--neutral: #939190;
$theme__color--destructive: #c72525;
$theme__color--confirmative: #23a030;
$theme__color--cautionary: #d1921c;
```

## colors.scss
This file contains all the color styles you will be using throughout your app. To use color styles use varibales starting with $color__ .You can add new color variables on this file to use throughout your app.  

Color Usage
```css
$color__primary: $theme__color--primary
```
You should use **$color__primary** when you want to use your brand primary color not any variable named with **$theme__**

Programatically generated tones
```css
$tone__primary--100: primary-color-tone($color__primary, 0);
```
Tones are generated using an scss function so you don't have to define them yourself. Tones are named begining with $tone__ and ending with 0, 10, 20...90, 95, 100 with 100 being the lightest and 0 being the darkest. 

$tone_ variables also should NOT be used anywhere. 

Color Usage $color__ styles
```css
$color__primary: $theme__color--primary
$color__surface__container--lowest: $color__neutral--100;
$color__surface__container--low: $color__neutral--95;
$color__surface__container: $color__neutral--90;
$color__on--surface: $color__neutral--10;
$color__on--surface--var: $color__neutral--30;
```
The color system is using the Google Material 3 color system and naming convention. To use the colors in your app, only use color variables beginning with $color__
