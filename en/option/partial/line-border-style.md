
{{ target: partial-line-border-style }}

{{ if: ${type} === 'border' }}
#${prefix} borderType(string|number|Array) = ${defaultType|default("'solid'")}
{{ elif: ${type} === 'text' }}
#${prefix} textBorderType(string|number|Array) = ${defaultType|default("'solid'")}
{{ else }}
#${prefix} type(string|number|Array) = ${defaultType|default("'solid'")}
{{ /if }}

{{ if: ${type} === 'border' }}
${name} border type.
{{ elif: ${type} === 'text' }}
Stroke line type of the text.
{{ else }}
line type.
{{ /if }}

Possible values are:
+ `'solid'`
+ `'dashed'`
+ `'dotted'`

<ExampleUIControlEnum default="${defaultType|default('solid')}" options="solid,dashed,dotted" />
<ExampleUIComponentInputSelect options="solid,dashed,dotted" />
<ExampleUIGroupLine_Style />

Since `v5.0.0`, it can also be a number or a number array to specify the [dash array](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/stroke-dasharray) of the line. With {{ if: ${type} === 'border' }}
`borderDashOffset`
{{ elif: ${type} === 'text' }}
`textBorderDashOffset`
{{ else }}
`dashOffset`
{{ /if }}, we can make the line style more flexible.

For example：
```ts
{
{{ if: ${type} === 'border' }}borderType{{ elif: ${type} === 'text' }}textBorderType{{ else }}type{{ /if }}: [5, 10],
{{ if: ${type} === 'border' }}borderDashOffset{{ elif: ${type} === 'text' }}textBorderDashOffset{{ else }}dashOffset{{ /if }}: 5
}
```

{{ if: ${type} === 'border' }}
#${prefix} borderDashOffset(number) = ${defaultDashOffset|default(0)}
{{ elif: ${type} === 'text' }}
#${prefix} textBorderDashOffset(number) = ${defaultDashOffset|default(0)}
{{ else }}
#${prefix} dashOffset(number) = ${defaultDashOffset|default(0)}
{{ /if }}

{{ use: partial-version(
    version = "5.0.0"
) }}

To set the line dash offset. With {{ if: ${type} === 'border' }}
`borderType`
{{ elif: ${type} === 'text' }}
`textBorderType`
{{ else }}
`type`
{{ /if }}, we can make the line style more flexible.

<ExampleUIControlNumber min="0" step="1" default="${defaultDashOffset|default(0)}" />
<ExampleUIComponentInputNumber min="0" step="1" />
<ExampleUIGroupLine_Style />

Refer to MDN [lineDashOffset](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/lineDashOffset) for more details.

{{ if: !${noCap} }}
{{ if: ${type} === 'border' }}
#${prefix} borderCap(string) = ${defaultCap|default("'butt'")}
{{ elif: ${type} === 'text' }}
{{! Text border does not support cap, skip }}
{{ else }}
#${prefix} cap(string) = ${defaultCap|default("'butt'")}
{{ /if }}

{{ if: ${type} !== 'text' }}
{{ use: partial-version(
    version = "5.0.0"
) }}

To specify how to draw the end points of the line.
Possible values are:
+ `'butt'`: The ends of lines are squared off at the endpoints.
+ `'round'`: The ends of lines are rounded.
+ `'square'`: The ends of lines are squared off by adding a box with an equal width and half the height of the line's thickness.

<ExampleUIControlEnum default="${defaultCap|default('butt')}" options="butt,round,square" />
<ExampleUIComponentInputSelect options="butt,round,square" />
<ExampleUIGroupLine_Style />

Default value is `'butt'`. Refer to MDN [lineCap](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/lineCap) for more details.
{{ /if }}
{{ /if }}

{{ if: !${noJoin} }}
{{ if: ${type} === 'border' }}
#${prefix} borderJoin(string) = ${defaultJoin|default("'bevel'")}
{{ elif: ${type} === 'text' }}
{{! Text border does not support join, skip }}
{{ else }}
#${prefix} join(string) = ${defaultJoin|default("'bevel'")}
{{ /if }}

{{ if: ${type} !== 'text' }}
{{ use: partial-version(
    version = "5.0.0"
) }}

To determine the shape used to join two line segments where they meet.

Possible values are:
+ `'bevel'`: Fills an additional triangular area between the common endpoint of connected segments, and the separate outside rectangular corners of each segment.
+ `'round'`: Rounds off the corners of a shape by filling an additional sector of disc centered at the common endpoint of connected segments. The radius for these rounded corners is equal to the line width.
+ `'miter'`: Connected segments are joined by extending their outside edges to connect at a single point, with the effect of filling an additional lozenge-shaped area. This setting is affected by the {{ if: ${type} === 'border' }}
`borderMiterLimit`
{{ else }}
`miterLimit`
{{ /if }} property.

<ExampleUIControlEnum default="${defaultJoin|default('bevel')}" options="bevel,round,miter" />
<ExampleUIComponentInputSelect options="bevel,round,miter" />
<ExampleUIGroupLine_Style />

Default value is `'bevel'`. Refer to MDN [lineJoin](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/lineJoin) for more details.
{{ /if }}
{{ /if }}

{{ if: !${noMiterLimit} }}
{{ if: ${type} === 'border' }}
#${prefix} borderMiterLimit(number) = ${defaultMiterLimit|default(10)}
{{ elif: ${type} === 'text' }}
{{! Text border does not support miter limit, skip }}
{{ else }}
#${prefix} miterLimit(number) = ${defaultMiterLimit|default(10)}
{{ /if }}

{{ if: ${type} !== 'text' }}
{{ use: partial-version(
    version = "5.0.0"
) }}

To set the miter limit ratio. Only works when {{ if: ${type} === 'border' }}
`borderJoin`
{{ else }}
`join`
{{ /if }} is set as `miter`.

<ExampleUIControlNumber min="0" step="1" default="${defaultMiterLimit|default(10)}" />
<ExampleUIComponentInputNumber min="0" step="1" />
<ExampleUIGroupLine_Style />

Default value is `10`. Negative、`0`、`Infinity` and `NaN` values are ignored.

Refer to MDN [miterLimit](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/miterLimit) for more details.
{{ /if }}
{{ /if }}