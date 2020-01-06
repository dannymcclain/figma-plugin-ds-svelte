# Figma Plugin DS Svelte

WORK IN PROGRESS—This is a Svelte version of the Figma Plugin DS specifically for use in creating Figma Plugins. I decided to create this because Svelte seems like a great lightweight approach well suited for creating Figma plugins, and also improves the developer experience when compared to my vanilla JS Figma Plugin DS due to simplified markup.

You can also get started with [Figsvelte](https://github.com/thomas-lowry/figsvelte), a boilerplate for Figma plugins that already has this library setup as a dependency.

## Installation

To install into your own Svelte project.
`npm -D figma-plugin-ds-svelte`

## To use

```javascript
//import the global css which includes Figma color, spacing, and type vars
//also includes a basic set of utility classes
import { GlobalCSS } from 'figma-plugin-ds-svelte';

//import the desired components
import { Button, Input, SelectMenu } from 'figma-plugin-ds-svelte';
```

---

## Components
_All components can accept class props to add global or utility classes to each component_

* [Button](#Button)
* [Checkbox](#Checkbox)

---

### Button
```javascript
import { Button } from 'figma-plugin-ds-svelte';
```
```html
<Button on:click={funcName}>Label</Button>
<Button on:click={funcName} variant="secondary">Label</Button>
<Button on:click={funcName} variant="secondary" destructive>Label</Button>
<Button on:click={funcName} disabled>Label</Button>
```
**Props**

| Prop           | Type    | Options/notes                                                   |
|:---------------|:--------|:----------------------------------------------------------------|
| `on:click`     | Func    | Assign a function to execute on click. Ex: `on:click={funcName}`|
| `variant`      | String  | Default: `"primary"`, Options: `"secondary"`, `"tertiary"`      |
| `disabled`     | Boolean | Default: `false`                                                |
| `desctructive` | Boolean | Default: `false`                                                |

---

### Checkbox
```javascript
import { Checkbox } from 'figma-plugin-ds-svelte';
```
```html
<Checkbox>Label</Checkbox>
<Checkbox checked>Label</Checkbox>
<Checkbox disabled>Label</Checkbox>
```
**Props**]

| Prop       | Type    | Options/notes                                                                            |
|:-----------|:--------|:-----------------------------------------------------------------------------------------|
| `on:change`| Func    | Funtion to execute on change. Ex: `on:change={funcName}`                                 |
| `value`    | Boolean | Default: `false`;                                                                        |
| `checked`  | Boolean | Default: `false`; You can bind the value when checked to a var. `bind:checked={varName}` |
| `disabled` | Boolean | Default: `false`                                                                         |

---

### Disclosure
```javascript
import { Disclosure, DisclosureItem } from 'figma-plugin-ds-svelte';
```
```html
<Disclosure>
  <DisclosureItem title="Item 1" open>Content here</DisclosureItem>
  <DisclosureItem title="Item 2">Content here</DisclosureItem>
  <DisclosureItem title="Item 3">Content here</DisclosureItem>
</Disclosure>
```
**Props**

| Prop       | Type    | Options/notes                                                     |
|:-----------|:--------|:------------------------------------------------------------------|
| `title`    | String  | Title of disclosure item                                          |
| `open`     | Boolean | Default: `false`; Only one disclosure item can be opened at once  |
| `section`  | Boolean | Default: `false`; Bold section header for disclosure title        |

---

### Icon
```javascript
//You need to import the icon component + whatever icons you want to use,
//pass the names of your icon modules to the iconName prop in the Icon component
import { Icon, IconName } from 'figma-plugin-ds-svelte';

//You can also import your own svg icon (32x32) and pass it to the icon component
import SvgName from './src/directory/image.svg';

//Example
import { Icon, IconVisible, IconSpinner } from 'figma-plugin-ds-svelte';
```
```html
<Icon iconName={IconVisible} color="black"/>
<Icon iconName={IconSpinner} color="blue" spin/>
<Icon iconText="W" color="blue"/>
```
**Props**

| Prop       | Type    | Options/notes                                                                                |
|:-----------|:--------|:---------------------------------------------------------------------------------------------|
| `iconName` | Var     | Pass an imported SVG to this prop. `iconName={IconImport}`                                   |
| `iconText` | String  | Pass a text character to use instead of an icon. Ex: width and height inputs `iconText="W"`  |
| `color`    | String  | Pass the name of any Figma color var to this prop. `color="blue"`                            |
| `spin`     | Boolean | Default: `false`; This will rotate the icon in an endless loop.                              |

---

### Icon Button
```javascript
//use this component as you would an Icon, it accepts the same props (except color)
import { IconButton } from 'figma-plugin-ds-svelte';
```
```html
<IconButton on:click={funcName} iconName={IconVisible}/>
<IconButton on:click={funcName} iconName={IconVisible} selected/>
<IconButton on:click={funcName} iconText="@"/>
```
**Props**

| Prop       | Type    | Options/notes                                                    |
|------------|---------|------------------------------------------------------------------|
| `on:click` | String  | Assign a function to execute on click. Ex: `on:click={funcName}` |
| `selected` | Boolean | Default: `false`                                                 |
| `iconName` | String  | _See Icon component for usage._                                  |
| `IconText` | String  | _See Icon component for usage._                                  |
| `spin`     | Boolean | _See Icon component for usage._                                  |

---

### Input
```javascript
import { Input } from 'figma-plugin-ds-svelte';

//var to define and store value
var inputValue = 'Default value'; 
```
```html
<Input bind:value={inputValue}/>
<Input bind:value={inputValue} disabled/>
<Input placeholder="Enter some info..."/>

<!-- You can also pass Icon props to use the icon component inside the input -->
<Input iconName={IconName} />
<Input iconName={IconSpinner} spin placeholder="Fetching data..." />

<!-- Force borders on the input -->
<Input value="Value" borders/>
```
**Props**

| Prop          | Type    | Options/notes                                                      |
|:--------------|:--------|:-------------------------------------------------------------------|
| `on:change`   | Func    | Funtion to execute on change. Ex: `on:change={funcName}`           |
| `value`       | String  | Value that will get populated by user or specify predefined value. You can also bind this to a variable. |
| `placeholder` | String  | Placeholder text.                                                  |
| `borders`     | Boolean | Default: `false`; Force a border on the input field.               |
| `disabled`    | Boolean | Default: `false`                                                   |
| `iconName`    | Var     | _See Icon component for usage._                                    |
| `iconText`    | String  | _See Icon component for usage._                                    |
| `spin`        | Boolean | _See Icon component for usage._                                    |

---

### Label + Section
```javascript
import { Label, SectionHeader } from 'figma-plugin-ds-svelte';
```
```html
<Label>Label name</Label>
<Section>Section name</Section>
```

---

### Onboarding Tip
```javascript
import { OnboardingTip } from 'figma-plugin-ds-svelte';
```
```html
<OnboardingTip iconName={IconStyles}>
  Tip text goes here
</OnboardingTip>
```
**Props**

| Prop       | Type    | Options/notes                   |
|:-----------|:--------|:--------------------------------|
| `iconName` | Var     | _See Icon component for usage._ |
| `iconText` | String  | _See Icon component for usage._ |
| `spin`     | Boolean | _See Icon component for usage._ |

---

### Radio Button
```javascript
import { Radio } from 'figma-plugin-ds-svelte';

//use bind:group, with a var to create a radio group and store the value of selected item
//set value if this var to same value as radio item to set initial selection
var radioValue;
```
```html
<Radio bind:group={radioValue} value="a">Label</Radio>
<Radio bind:group={radioValue} value="b">Label</Radio>
```
**Props**

| Prop       | Type    | Options/notes                                             |
|:-----------|:--------|:----------------------------------------------------------|
| `on:change`| Func    | Funtion to execute on change. Ex: `on:change={funcName}`  |
| `group`    | Var     | Pass name of var to store selected item from radio group. |
| `value`    | String  | Value of radio item.                                      |
| `disabled` | Boolean | Default: `false`                                          |

---

### Select Menu
```javascript
import { SelectMenu } from 'figma-plugin-ds-svelte';

//You will need to pass and bind an array of menu items to this
//Note: it is up to you to sort this array however you want
let menuItemArray = [
  { 'value': 'item1', 'label': 'Menu item 1', 'group': null, 'selected': false },
  { 'value': 'item2', 'label': 'Menu item 2 ', 'group': null, 'selected': false }
];

//use bind:value, with a var bind the data of the selected item
var selectedItem;
```
```html
<SelectMenu bind:menuItems={menuItemArray} bind:value={selectedItem}/>
<SelectMenu bind:menuItems={menuItemArray} bind:value={selectedItem} showGroupLabels/>
<SelectMenu bind:menuItems={menuItemArray} bind:value={selectedItem} iconName={IconBlend}/>
<SelectMenu bind:menuItems={menuItemArray} bind:value={selectedItem} disabled/>
```
**Props**

| Prop              | Type    | Options/notes                                                                                                                            |
|-------------------|---------|------------------------------------------------------------------------------------------------------------------------------------------|
| `on:change`       | Func    | Function to execute on change. Ex: `on:change={funcName}`                                                                                |
| `menuItems`       | Var     | Pass in array of menu item objects. See example above for format.  If you want to use option groups, update the group keys to a string.  |
| `value`           | Var     | Bind the value of the selected item to a var. Ex: `bind:value={selectedItem}`                                                       |
| `placeholder`     | String  | Override default placeholder text with a string when there is no item selected.                                                          |
| `showGroupLabels` | Boolean | Default: `false`; If you are using option groups, this will show the group labels.                                                       |
| `disabled`        | Boolean | Default: `false`                                                                                                                         |
| `macOSBlink`      | Boolean | Default: `false`; Easter egg, old school Mac OS triple blink on select.                                                                  |
| `iconName`        | Var     | _See Icon component for usage._                                                                                                          |
| `iconText`        | String  | _See Icon component for usage._                                                                                                          |

---

### Switch
```javascript
import { Switch } from 'figma-plugin-ds-svelte';

//use bind:group, with a var to create a radio group and store the value of selected item
//set value if this var to same value as radio item to set initial selection
var switchValue;
```
```html
<Switch value="value" bind:checked={switchValue}>Label</Switch>
```
**Props**

| Prop       | Type    | Options/notes                                                                            |
|:-----------|:--------|:-----------------------------------------------------------------------------------------|
| `on:change`| Func    | Funtion to execute on change. Ex: `on:change={funcName}`                                 |
| `value`    | Boolean | Default: `false`;                                                                        |
| `checked`  | Boolean | Default: `false`; You can bind the value when checked to a var. `bind:checked={varName}` |
| `disabled` | Boolean | Default: `false`                                                                         |

---

### Textarea
```javascript
import { Textarea } from 'figma-plugin-ds-svelte';
```
```html
<Textarea placeholder="Enter some text"></Textarea>
```
**Props**

| Prop          | Type    | Options/notes                                                         |
|:--------------|:--------|:----------------------------------------------------------------------|
| `on:change`   | Func    | Function to execute on change. Ex: `on:change={funcName}`             |
| `value`       | String  | Value of textarea. Can bind to a variable. Ex: `bind:value={someVar}` |
| `placeholder` | String  | Override default placeholder text with a string.                      |
| `rows`        | Int     | Default: `2`; Number of rows (height) to display.                     |
| `disabled`    | Boolean | Default: `false`                                                      |

---

### Type
```javascript
import { Type } from 'figma-plugin-ds-svelte';
```
```html
<Type size="large" weight="bold">Content here</Type>
```
**Props**

| Prop      | Type    | Options/notes                                                                          |
|:----------|:--------|:---------------------------------------------------------------------------------------|
| `size`    | String  | Default: `"small"`; Also accepts `"xsmall"`,`"large"`, `"xlarge"`                      |
| `weight`  | String  | Default: `"normal"`; Also accepts `"medium"`,`"bold"`                                  |
| `color`   | String  | Default: `"black8"`; Pass the name of any Figma color var to this prop. `color="blue"`, Default color is white when inverse is `true` and no value specified |
| `inverse` | Boolean | Default: `false`; Optimizes letter-spacing for light on dark applications.             |

---

## Tokens

**Color**

| Name          | Var               | Type             | Notes                                                         |
|:--------------|:------------------|:-----------------|:--------------------------------------------------------------|
| blue          | `--blue`          | Accent           | Ex: primary button, hyperlinks, focus/selected states         |
| purple        | `--purple`        | Accent           | Ex: components/instances                                      |
| hot-pink      | `--hot-pink`      | Accent           | Ex: smart selection handles                                   |
| green         | `--green`         | Accent           | Ex: Toolbar selections                                        |
| red           | `--red`           | Accent           | Ex: Error                                                     |
| yellow        | `--yellow`        | Accent           | Ex: Caution/warning                                           |
| black         | `--black`         | Basic foreground | Ex: active states                                             |
| black8        | `--black8`        | Basic foreground | 80% black, ex: most common black used in UI text and icons    |
| black8-opaque | `black8-opaque`   | Basic foreground | Opaque version of black8                                      |
| black3        | `--black3`        | Basic foreground | 30% black, ex: lower priority messages, disabled states       |
| black3-opaque | `--black3-opaque` | Basic foreground | Opaque version of black3                                      |
| white         | `--white`         | Basic foreground | Used in same way as black8, but on dark backgrounds           |
| white8        | `--white8`        | Basic foreground | Rarely used, only in toolbar                                  |
| white4        | `--white4`        | Basic foreground | Used in same way as black3, Ex: option group headers in menus |
| white         | `--white`         | Basic background | (Duplicate) White is also the most common background color    |
| grey          | `--grey`          | Basic background | Used behind controls in active state                          |
| silver        | `--silver`        | Basic background | Ex: horizontal separators, default canvas background          |
| hud           | `--hud`           | Basic background | Ex: background for menus                                      |
| toolbar       | `--toolbar`       | Basic background | Ex: background for the toolbar                                |
| black1        | `--black1`        | Special          | Ex: input placeholder underline, textarea border              |
| blue3         | `--blue3`         | Special          | Ex: text range selection in inputs                            |
| purple4       | `--purple4`       | Special          | Ex: disabled components/instances                             |
| hover-fill    | `--hover-fill`    | Special          | Hover state for items without borders, ex: icon button        |
| selection-a   | `--selection-a`   | Special          | Selected cells, ex: selected top level layer                  |
| selection-b   | `--selection-b`   | Special          | Selected cells, ex: selected child layers                     |
| white3        | `--white3`        | Special          | Ex: menu separators                                           |


**Type**

| Property         | Var                                | Value               | Notes                                                        |
|:-----------------|:-----------------------------------|:--------------------|:-------------------------------------------------------------|
| `font-family`    | `--font-stack`                     | 'Inter', sans-serif | Default font everywhere                                      |
| `font-size`      | `--font-size-xsmall`               | 11px                | Most common font size                                        |
| `font-size`      | `--font-size-small`                | 12px                | Used in menus                                                |
| `font-size`      | `--font-size-large`                | 13px                | Rarely used in editor                                        |
| `font-size`      | `--font-size-xlarge`               | 14px                | Rarely used in editor                                        |
| `font-weight`    | `--font-weight-normal`             | 400                 |                                                              |
| `font-weight`    | `--font-weight-medium`             | 500                 |                                                              |
| `font-weight`    | `--font-weight-bold`               | 600                 |                                                              |
| `line-height`    | `--font-line-height`               | 16px                | For use with xsmall and small font sizes                     |
| `line-height`    | `--font-line-height-large`         | 24px                | For use with large and xlarge font sizes                     |
| `letter-spacing` | `--font-letter-spacing-pos-xsmall` | .005em              | Optimized letter spacing for xsmall text on light background |
| `letter-spacing` | `--font-letter-spacing-neg-xsmall` | .01em               | Optimized letter spacing for xsmall text on dark background  |
| `letter-spacing` | `--font-letter-spacing-pos-small`  | 0                   | Optimized letter spacing for small text on light background  |
| `letter-spacing` | `--font-letter-spacing-neg-small`  | .005em              | Optimized letter spacing for small text on dark background   |
| `letter-spacing` | `--font-letter-spacing-pos-large`  | -0.0025em           | Optimized letter spacing for large text on light background  |
| `letter-spacing` | `--font-letter-spacing-neg-large`  | .0025em             | Optimized letter spacing for large text on dark background   |
| `letter-spacing` | `--font-letter-spacing-pos-xlarge` | -.001em             | Optimized letter spacing for xlarge text on light background |
| `letter-spacing` | `--font-letter-spacing-neg-xlarge` | -.001em             | Optimized letter spacing for xlarge text on dark background  |

**Border Radius**

| Var                     | Value | Notes                                 |
|:------------------------|:------|:--------------------------------------|
| `--border-radius-small` | 2px   | Ex: menus, input borders, icon button |
| `--border-radius-med`   | 5px   | Ex: visual bell, toasts               |
| `--border-radius-large` | 6px   | Ex: buttons                           |

**Shadows**

| Var                         | Notes                       |
|:----------------------------|:----------------------------|
| `--shadow-hud`              | Ex: menus, tooltips, toasts |
| `--shadow-floating-window:` | Ex: modal, dialog           |

**Sizes**

| Var              | Value |
|:-----------------|:------|
| `--size-xxsmall` | 8px   |
| `--size-xsmall`  | 16px  |
| `--size-small`   | 24px  |
| `--size-medium`  | 32px  |
| `--size-large`   | 40px  |
| `--size-xlarge`  | 48px  |
| `--size-xxlarge` | 64px  |
| `--size-huge`    | 80px  |
