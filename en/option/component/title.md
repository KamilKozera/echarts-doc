
{{ target: component-title }}

# title(Object)

Title component, including main title and subtitle.

In ECharts 2.x, a single instance of ECharts could contains one title component at most. However, in ECharts 3, there could be one or more than one title components. It is more useful when multiple diagrams in one instance all need titles.

**Here are some instances of different animation easing functions, among which every instance has a title component: **
~[700x400](${galleryViewPath}line-easing&edit=1&reset=1)

{{ use: partial-component-id(
    prefix = "#"
) }}

## show(boolean) = true

Whether to show the title component. Default value is `true`.

<ExampleUIControlBoolean default="true" />
<ExampleUIComponentInputSwitch />
<ExampleUIGroupDisplay />

Set this to `false` to prevent the title from showing

## text(string) = ''

The main title text, supporting for `\n` for newlines.

<ExampleUIControlText default="" />
<ExampleUIComponentInputText />
<ExampleUIGroupMain_Title />

## link(string) = ''

The hyper link of main title text.

<ExampleUIControlText default="" />
<ExampleUIComponentInputText />
<ExampleUIGroupMain_Title />

## target(string) = 'blank'

Open the hyper link of main title in specified tab.

**options: **

+ `'self'` opening it in current tab

+ `'blank'` opening it in a new tab

<ExampleUIControlEnum options="'self','blank'" default="'blank'" />
<ExampleUIComponentInputSelect options="'self','blank'" />
<ExampleUIGroupMain_Title />

## textStyle(Object)

Text style of the main title.

<ExampleUIGroupMain_Title_Style />

{{ use: partial-text-style(
    prefix = "##",
    name = "main title",
    defaultFontSize = 18,
    defaultFontWeight = "'bolder'",
    defaultColor = "'#333'",
    noAlign = true,
    noVerticalAlign = true,
    noBox = true
) }}

## subtext(string) = ''

Subtitle text, supporting for `\n` for newlines.

<ExampleUIControlText default="" />
<ExampleUIComponentInputText />
<ExampleUIGroupSubtitle />

## sublink(string) = ''

The hyper link of subtitle text.

<ExampleUIControlText default="" />
<ExampleUIComponentInputText />
<ExampleUIGroupSubtitle />

## subtarget(string) = 'blank'

Open the hyper link of subtitle in specified tab, options:

+ `'self'` opening it in current tab

+ `'blank'` opening it in a new tab

<ExampleUIControlEnum options="'self','blank'" default="'blank'" />
<ExampleUIComponentInputSelect options="'self','blank'" />
<ExampleUIGroupSubtitle />

## subtextStyle(Object)

Text style of the subtitle.

<ExampleUIGroupSubtitle_Style />

{{ use: partial-text-style(
    prefix = '##',
    name = "subtitle",
    defaultColor = "'#aaa'",
    noBox = true
) }}

## textAlign(string) = 'auto'

The horizontal align of the component (including "text" and "subtext").

Optional values: `'auto'`, `'left'`, `'right'`, `'center'`.

<ExampleUIControlEnum options="auto,left,center,right" default="auto" />
<ExampleUIComponentInputSelect options="auto,left,center,right" />
<ExampleUIGroupAlignment />

## textVerticalAlign(string) = 'auto'

The vertical align of the component (including "text" and "subtext").

Optional values: `'auto'`, `'top'`, `'bottom'`, `'middle'`.

<ExampleUIControlEnum options="auto,top,middle,bottom" default="auto" />
<ExampleUIComponentInputSelect options="auto,top,middle,bottom" />
<ExampleUIGroupAlignment />

## triggerEvent(boolean) = false

Set this to `true` to enable triggering events for the title component.

<ExampleUIControlBoolean default="false" />
<ExampleUIComponentInputSwitch />
<ExampleUIGroupInteraction />

## padding(number|Array) = 5

Padding around the title content.

<ExampleUIGroupLayout />

{{ use: partial-padding(
    componentName = "title"
) }}

## itemGap(number) = 10

The gap between the main title and subtitle.

<ExampleUIControlNumber min="0" default="10" step="1" />
<ExampleUIComponentInputNumber min="0" step="1" />
<ExampleUIGroupLayout />

{{ use: partial-rect-layout(
    componentName = "title ",
    defaultZ = 2,
    defaultZLevel = 0
) }}

{{ use: partial-component-common-style(
    componentName = "title",
    prefix = '#',
    defaultBorderWidth = "0",
    hasBorderRadius = true
) }}