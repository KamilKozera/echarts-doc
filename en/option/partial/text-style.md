
{{ target: partial-simple-text-style }}

{{ use: partial-text-style(
    prefix = ${prefix},
    name = ${name},
    defaultColor = ${defaultColor},
    defaultFontSize = ${defaultFontSize},
    defaultFontWeight = ${defaultFontWeight},
    defaultLineHeight = ${defaultLineHeight},
    noAlign = true,
    noVerticalAlign = true,
    noRich = true,
    noBox = true
) }}

{{ target: partial-text-style }}

{{ use: partial-text-style-base-item(
    prefix = ${prefix},
    name = ${name},
    defaultColor = ${defaultColor},
    defaultPadding = ${defaultPadding},
    defaultFontSize = ${defaultFontSize},
    defaultFontWeight = ${defaultFontWeight},
    defaultLineHeight = ${defaultLineHeight},
    defaultAlign = ${defaultAlign},
    defaultVerticalAlign = ${defaultVerticalAlign},
    noAlign = ${noAlign},
    noVerticalAlign = ${noVerticalAlign},
    noBox = ${noBox},
    enableAutoColor = ${enableAutoColor}
) }}

#${prefix} width(number)

Width of text block.

<ExampleUIControlNumber min="1" step="1" />
<ExampleUIComponentInputNumber min="1" step="1" />
<ExampleUIGroupSize />

#${prefix} height(number)

Height of text block.

<ExampleUIControlNumber min="1" step="1" />
<ExampleUIComponentInputNumber min="1" step="1" />
<ExampleUIGroupSize />

#${prefix} overflow(string) = 'none'

Determine how to display the text when it's overflow. Available when `width` is set.

+ `'truncate'` Truncate the text and trailing with `ellipsis`.
+ `'break'` Break by word
+ `'breakAll'` Break by character.

<ExampleUIControlEnum options="none,truncate,break,breakAll" default="none" />
<ExampleUIComponentInputSelect options="none,truncate,break,breakAll" />
<ExampleUIGroupOverflow />

#${prefix} ellipsis(string) = '...'

Ellipsis to be displayed when `overflow` is set to `truncate`.

+ `'truncate'` Truncate the overflow lines.

<ExampleUIControlText default="'...'" />
<ExampleUIComponentInputText />
<ExampleUIGroupOverflow />

{{ if: !${noRich} }}
#${prefix} rich(Object)

"Rich text styles" can be defined in this `rich` property. For example:

```ts
label: {
    // Styles defined in 'rich' can be applied to some fragments
    // of text by adding some markers to those fragment, like
    // `{styleName|text content text content}`.
    // `'\n'` is the newline character.
    formatter: [
        '{a|Style "a" is applied to this snippet}'
        '{b|Style "b" is applied to this snippet}This snippet use default style{x|use style "x"}'
    ].join('\n'),

    rich: {
        a: {
            color: 'red',
            lineHeight: 10
        },
        b: {
            backgroundColor: {
                image: 'xxx/xxx.jpg'
            },
            height: 40
        },
        x: {
            fontSize: 18,
            fontFamily: 'Microsoft YaHei',
            borderColor: '#449933',
            borderRadius: 4
        },
        ...
    }
}
```

For more details, see [Rich Text](tutorial.html#Rich%20Text) please.

<ExampleUIGroupRich_Text_Styles />

##${prefix} <style_name>(Object)

Define styles for a rich text tag name.

{{ use: partial-text-style-base-item(
    prefix = ${prefix} + '##',
    enableAutoColor = ${enableAutoColor}
) }}
{{ /if }}

{{ target: partial-text-style-base-item }}

<ExampleUIGroupRich_Text_Styles />

#${prefix} color(Color) = ${defaultColor|default("'#fff'")}

${name} text color.

<ExampleUIControlColor default="${defaultColor|default("'#fff'")}" />
<ExampleUIComponentInputColor />

{{ if: ${enableAutoColor} }}
{{ use: partial-text-style-auto-color-desc() }}
{{ /if }}

<ExampleUIGroupFont />

#${prefix} fontStyle(string) = 'normal'

${name} font style.

Options are:
+ `'normal'`
+ `'italic'`
+ `'oblique'`

<ExampleUIControlEnum default="normal" options="normal,italic,oblique" />
<ExampleUIComponentInputSelect options="normal,italic,oblique" />
<ExampleUIGroupFont />

#${prefix} fontWeight(string|number) = ${defaultFontWeight|default("'normal'")}

${name} font thick weight.

Options are:
+ `'normal'`
+ `'bold'`
+ `'bolder'`
+ `'lighter'`
+ 100 | 200 | 300 | 400...

<ExampleUIControlEnum default="${defaultFontWeight|default("'normal'")}" options="normal,bold,bolder,lighter,100,200,300,400,500,600,700,800,900" />
<ExampleUIComponentInputSelect options="normal,bold,bolder,lighter,100,200,300,400,500,600,700,800,900" />
<ExampleUIGroupFont />

#${prefix} fontFamily(string) = 'sans-serif'

${name} font family.

Can also be 'serif' , 'monospace', ...

<ExampleUIControlEnum default="sans-serif" options="sans-serif,serif,monospace,Arial,Courier New,Microsoft YaHei" />
<ExampleUIComponentInputSelect options="sans-serif,serif,monospace,Arial,Courier New,Microsoft YaHei" />
<ExampleUIGroupFont />

#${prefix} fontSize(number) = ${defaultFontSize|default(12)}

${name} font size.

<ExampleUIControlNumber default="${defaultFontSize|default(12)}" min="1" step="1" />
<ExampleUIComponentInputNumber min="1" step="1" />
<ExampleUIGroupFont />

{{ if: !${noAlign} }}
#${prefix} align(string) = ${defaultAlign}

Horizontal alignment of text, automatic by default.

Options are:
+ `'left'`
+ `'center'`
+ `'right'`

<ExampleUIControlEnum options="left,center,right" default="${defaultAlign|default(null)}" />
<ExampleUIComponentInputSelect options="left,center,right" />
<ExampleUIGroupAlignment />

{{ use: partial-text-style-rich-inherit(
    name = 'align',
    value = 'right'
) }}
{{ /if }}

{{ if: !${noVerticalAlign} }}
#${prefix} verticalAlign(string) = ${defaultVerticalAlign}

Vertical alignment of text, automatic by default.

Options are:
+ `'top'`
+ `'middle'`
+ `'bottom'`

<ExampleUIControlEnum options="top,middle,bottom" default="${defaultVerticalAlign|default(null)}" />
<ExampleUIComponentInputSelect options="top,middle,bottom" />
<ExampleUIGroupAlignment />

{{ use: partial-text-style-rich-inherit(
    name = 'verticalAlign',
    value = 'bottom'
) }}
{{ /if }}

#${prefix} lineHeight(number) = ${defaultLineHeight|default('')}

Line height of the text fragment.

<ExampleUIControlNumber min="0" step="1" default="${defaultLineHeight|default(null)}" />
<ExampleUIComponentInputNumber min="0" step="1" />
<ExampleUIGroupLayout />

{{ use: partial-text-style-rich-inherit(
    name = 'lineHeight',
    value = 56
) }}

{{ if: !${noBox} }}
#${prefix} backgroundColor(string|Object) = 'transparent'

Background color of the text fragment.

Can be color string, like `'#123234'`, `'red'`, `'rgba(0,23,11,0.3)'`.

Or image can be used, for example:

```ts
backgroundColor: {
    image: 'xxx/xxx.png'
    // It can be URL of a image,
    // or dataURI,
    // or HTMLImageElement,
    // or HTMLCanvasElement.
}
```

`width` or `height` can be specified when using background image, or
auto adapted by default.

<ExampleUIControlColor default="transparent" />
<ExampleUIComponentInputColor />
<ExampleUIGroupBox_Style />

{{ if: ${enableAutoColor} }}
{{ use: partial-text-style-auto-color-desc() }}
{{ /if }}

#${prefix} borderColor(Color)

Border color of the text fragment.

<ExampleUIControlColor />
<ExampleUIComponentInputColor />
<ExampleUIGroupBox_Style />

{{ if: ${enableAutoColor} }}
{{ use: partial-text-style-auto-color-desc() }}
{{ /if }}

#${prefix} borderWidth(number) = 0

Border width of the text fragment.

<ExampleUIControlNumber default="0" min="0" step="0.5" />
<ExampleUIComponentInputNumber min="0" step="0.5" />
<ExampleUIGroupBox_Style />

{{ use: partial-line-border-style(
    prefix = ${prefix},
    type = 'border',
    name = 'the text fragment',
    defaultType = ${defaultType},
    noCap = true,
    noJoin = true,
    noMiterLimit = true
) }}

#${prefix} borderRadius(number|Array) = 0

Border radius of the text fragment.

<ExampleUIControlVector default="0" min="0" dims="LT,RT,RB,LB" />
<ExampleUIComponentInputVector dims="LT,RT,RB,LB" min="0" />
<ExampleUIGroupBox_Style />

#${prefix} padding(number|Array) = ${defaultPadding|default(0)}

Padding of the text fragment, for example:

+ `padding: [3, 4, 5, 6]`: represents padding of `[top, right, bottom, left]`.
+ `padding: 4`: represents `padding: [4, 4, 4, 4]`.
+ `padding: [3, 4]`: represents `padding: [3, 4, 3, 4]`.

Notice, `width` and `height` specifies the width and height of the content, without `padding`.

<ExampleUIControlVector default="${defaultPadding|default(0)}" min="0" dims="T,R,B,L" />
<ExampleUIComponentInputVector dims="T,R,B,L" min="0" />
<ExampleUIGroupLayout />

#${prefix} shadowColor(Color) = 'transparent'

Shadow color of the text block.

<ExampleUIControlColor default="transparent" />
<ExampleUIComponentInputColor />
<ExampleUIGroupBox_Shadow />

#${prefix} shadowBlur(number) = 0

Show blur of the text block.

<ExampleUIControlNumber default="0" min="0" step="0.5" />
<ExampleUIComponentInputNumber min="0" step="0.5" />
<ExampleUIGroupBox_Shadow />

#${prefix} shadowOffsetX(number) = 0

Shadow X offset of the text block.

<ExampleUIControlNumber default="0" step="0.5" />
<ExampleUIComponentInputNumber step="0.5" />
<ExampleUIGroupBox_Shadow />

#${prefix} shadowOffsetY(number) = 0

Shadow Y offset of the text block.

<ExampleUIControlNumber default="0" step="0.5" />
<ExampleUIComponentInputNumber step="0.5" />
<ExampleUIGroupBox_Shadow />

{{ /if }}

#${prefix} width(number|string)

Width of the text block. It is the width of the text by default. In most cases, there is no need to specify it. You may want to use it in some cases like make simple table or using background image (see `backgroundColor`).

Notice, `width` and `height` specifies the width and height of the content, without `padding`.

`width` can also be percent string, like `'100%'`, which represents the percent of `contentWidth` (that is, the width without `padding`) of its container box. It is based on `contentWidth` because that each text fragment is layout based on the `content box`, where it makes no sense that calculating width based on `outerWith` in prectice.

Notice, `width` and `height` only work when `rich` specified.

<ExampleUIControlText />
<ExampleUIComponentInputText />
<ExampleUIGroupSize />

#${prefix} height(number|string)

Height of the text block. It is the width of the text by default. You may want to use it in some cases like using background image (see `backgroundColor`).

Notice, `width` and `height` specifies the width and height of the content, without `padding`.

Notice, `width` and `height` only work when `rich` specified.

<ExampleUIControlText />
<ExampleUIComponentInputText />
<ExampleUIGroupSize />

#${prefix} textBorderColor(Color)

Stroke color of the text.

<ExampleUIControlColor />
<ExampleUIComponentInputColor />
<ExampleUIGroupText_Stroke />

{{ if: ${enableAutoColor} }}
{{ use: partial-text-style-auto-color-desc() }}
{{ /if }}

#${prefix} textBorderWidth(number)

Stroke line width of the text.

<ExampleUIControlNumber min="0" step="0.5" />
<ExampleUIComponentInputNumber min="0" step="0.5" />
<ExampleUIGroupText_Stroke />

{{ use: partial-line-border-style(
    prefix = ${prefix},
    name = ${name},
    type = 'text',
    defaultType = ${defaultType},
    noCap = true,
    noJoin = true,
    noMiterLimit = true
) }}

#${prefix} textShadowColor(Color) = 'transparent'

Shadow color of the text itself.

<ExampleUIControlColor default="transparent" />
<ExampleUIComponentInputColor />
<ExampleUIGroupText_Shadow />

#${prefix} textShadowBlur(number) = 0

Shadow blue of the text itself.

<ExampleUIControlNumber default="0" min="0" step="0.5" />
<ExampleUIComponentInputNumber min="0" step="0.5" />
<ExampleUIGroupText_Shadow />

#${prefix} textShadowOffsetX(number) = 0

Shadow X offset of the text itself.

<ExampleUIControlNumber default="0" step="0.5" />
<ExampleUIComponentInputNumber step="0.5" />
<ExampleUIGroupText_Shadow />

#${prefix} textShadowOffsetY(number) = 0

Shadow Y offset of the text itself.

<ExampleUIControlNumber default="0" step="0.5" />
<ExampleUIComponentInputNumber step="0.5" />
<ExampleUIGroupText_Shadow />

{{ target: partial-text-style-auto-color-desc }}

If set as `'inherit'`, the color will assigned as visual color, such as series color.

{{ target: partial-text-style-rich-inherit }}

If `${name}` is not set in `rich`, `${name}` in parent level will be used. For example:

```ts
{
    ${name}: ${value},
    rich: {
        a: {
            // `${name}` is not set, then it will be ${value}
        }
    }
}
```