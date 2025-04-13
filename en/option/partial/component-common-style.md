
{{ target: partial-component-common-style }}

#${prefix} backgroundColor(Color) = 'transparent'

Background color of ${componentName}, which is transparent by default.

<ExampleUIControlColor default="transparent" />
<ExampleUIComponentInputColor />
<ExampleUIGroupStyle />

> Color can be represented in RGB, for example `'rgb(128, 128, 128)'`. RGBA can be used when you need alpha channel, for example `'rgba(128, 128, 128, 0.5)'`. You may also use hexadecimal format, for example `'#ccc'`.

{{ if: ${needShow} }}
**Attention**: Works only if `show: true` is set.
{{ /if }}

#${prefix} borderColor(Color) = '#ccc'

Border color of ${componentName}. Support the same color format as backgroundColor.

<ExampleUIControlColor default="#ccc" />
<ExampleUIComponentInputColor />
<ExampleUIGroupStyle />

{{ if: ${needShow} }}
**Attention**: Works only if `show: true` is set.
{{ /if }}

#${prefix} borderWidth(number) = ${defaultBorderWidth|default(1)}

Border width of ${componentName}.

<ExampleUIControlNumber default="${defaultBorderWidth|default(1)}" min="0" step="0.5" />
<ExampleUIComponentInputNumber min="0" step="0.5" />
<ExampleUIGroupStyle />

{{ if: ${needShow} }}
**Attention**: Works only if `show: true` is set.
{{ /if }}

{{ if: ${hasBorderRadius} }}
{{ use: partial-border-radius(
    prefix = ${prefix}
) }}
{{ /if }}

{{ use: partial-style-shadow(
    prefix = ${prefix},
    needShow = true
) }}

{{ target: partial-border-radius }}

#${prefix} ${propName|default('borderRadius')}(number|Array) = ${defaultBorderRadius|default(0)}

The radius of rounded corner. Its unit is px. And it supports use array to respectively specify the 4 corner radiuses.

{{ if: ${version} }}
{{ use: partial-version(
    version = ${version}
) }}
{{ /if }}

<ExampleUIControlVector min="0" dims="LT,RT,RB,LB" default="${defaultBorderRadius|default(0)}" />
<ExampleUIComponentInputVector dims="LT,RT,RB,LB" min="0" />
<ExampleUIGroupStyle />

For example:
```
${propName|default('borderRadius')}: 5, // consistently set the size of 4 rounded corners
${propName|default('borderRadius')}: [5, 5, 0, 0] // (clockwise upper left, upper right, bottom right and bottom left)
```

{{ target: partial-style-shadow }}

#${prefix} shadowBlur(number)

Shadow blur size. This attribute works only if `show: true` is set.

<ExampleUIControlNumber min="0" step="1" />
<ExampleUIComponentInputNumber min="0" step="1" />
<ExampleUIGroupShadow_Style />

#${prefix} shadowColor(Color)

Shadow color. Support same format as `color`. This attribute works only if `show: true` is set.

<ExampleUIControlColor />
<ExampleUIComponentInputColor />
<ExampleUIGroupShadow_Style />

#${prefix} shadowOffsetX(number) = 0

Offset distance on the horizontal direction of shadow. This attribute works only if `show: true` is set.

<ExampleUIControlNumber default="0" step="1" />
<ExampleUIComponentInputNumber step="1" />
<ExampleUIGroupShadow_Style />

#${prefix} shadowOffsetY(number) = 0

Offset distance on the vertical direction of shadow. This attribute works only if `show: true` is set.

<ExampleUIControlNumber default="0" step="1" />
<ExampleUIComponentInputNumber step="1" />
<ExampleUIGroupShadow_Style />