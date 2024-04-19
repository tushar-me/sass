# Sass Structure

```
sass/
|
|- abstracts/
|   |- _colors.scss      # Color Variables
|   |- _media-query.scss  # Media Query Variables
|   ...
|   |- _index.scss
|
|– base/
|   |– _reset.scss       # Reset/normalize
|   |– _typography.scss  # Typography rules
|   ...                  
|   |- _index.scss
|
|– components/
|   |– _buttons.scss     # Buttons
|   |– _carda.scss       # Cover
|   |– _titles.scss      # Titles
|   ...                  
|   |- _index.scss
|
|– layout/
|   |– _header.scss      # Header
|   |– _footer.scss      # Footer
|   |– _sidebar.scss     # Sidebar
|   |– _sidebar.scss     # Sidebar
|   |– _forms.scss       # Forms
|   ...                  
|   |- _index.scss
|
|– pages/
|   |– _home.scss        # Home specific styles
|   |– _contact.scss     # Contact specific styles
|   ...                  
|   |- _index.scss
|
|
`– app.scss            # Primary Sass file
```


 In every folder, there is a file, called `_index.scss`. It is there becuase you no longer need to import each file from the folder one by one. In `_index.scss` file, there should be only @forwards which is literally used to "forward" your files as a folder across other different files.

For example, in our case, in `abstracts/` folder, there are 3 different files except for `_index.scss` one. In `_index.scss` file, we can "forward" each file within that folder:

`_index.scss`

```sh
@forward 'variables';
@forward 'media-query';
@forward 'colors';
```

If you want to use all files within `abstracts/` folder, you can "use" them like this:

`app.scss`

```sh
@use 'abstracts';
```

Let's say you created some colors variables in your `_colors.scss` file. And, you want to use it in your `_buttons.scss` file to give some styling for buttons. What you can do is this:

`_buttons.scss`

```sh
@use "../abstracts" as *;
```


### ABSTRACTS FOLDER

The `abstracts/` folder gathers all Sass tools and helpers used across the project. Every global variable, function, mixin and placeholder should be put in here.

The rule of thumb for this folder is that it should not output a single line of CSS when compiled on its own.

### BASE FOLDER

The `base/` folder holds what we might call the boilerplate code for the project. In there, you might find the reset file, some typographic rules, and probably a stylesheet, defining some standard styles for commonly used HTML elements.

### COMPONENTS FOLDER

For smaller components, there is the `components/` folder. While `layout/` is macro (defining the global wireframe), `components/` is more focused on widgets. It contains all kind of specific modules like a slider, a loader, a widget, and basically anything along those lines. There are usually a lot of files in `components/` since the whole site/application should be mostly composed of tiny modules.

### LAYOUT FOLDER

The `layout/` folder contains everything that takes part in laying out the site or application. This folder could have stylesheets for the main parts of the site (header, footer, navigation, sidebar…), the grid system or even CSS styles for all the forms.

### PAGES FOLDER

If you have page-specific styles, it is better to put them in a `pages/` folder, in a file named after the page. For instance, it’s not uncommon to have very specific styles for the home page hence the need for a `_home.scss` file in `pages/`.
