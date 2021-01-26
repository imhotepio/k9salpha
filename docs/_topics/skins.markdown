---
layout: section
---

[<img src="/assets/sections/cow.png" align="right" width="150" height="auto"/>](/topics)

<br/>
<br/>
<br/>

# Skins

You can style K9s𝞪 based on your own sense of look and style. Skins are YAML files, that enable a user to change the K9s𝞪 presentation layer. Skin files live in your `$HOME/.k9s-alpha` folder for your respective Kubernetes contexts. You can specify a general skin file `$HOME/.k9s-alpha/default-skins.yml` that applies to all your contexts. Alternatively, you can have context specific skins that are located in `$HOME/.k9s-alpha/contexts/contextXXX/skins.yml`. If a skin file exists for your cluster then the skin will be loaded if not the default skin remains in effect. So if you want to have K9s𝞪 looking different on a per cluster basis and say your context is named `fred` then your skins file name should be named `$HOME/.k9s-alpha/contexts/fred/skins.yml`. Below is a sample skin file, more skins are available in the [skins](https://github.com/imhotepio/k9salpha/tree/master/skins) directory in the k9salpha repo.

Colors can be defined as named colors (see table below) or using an hex representation. To preserve your terminal session background color, we've added a color named `default` to indicate a transparent background color if so desired.

<div class="center">
  <img src="/assets/skins/dracula.png" align="center" width="800" height="auto">
  <br/>
  K9s𝞪 Dracula skin
</div>

<br/>
<div class="note">
  <i class="fas fa-skull"></i> Changes to the skin file layout will occur as more features are added, so thread accordingly!
</div>

<br/>

## <img src="/assets/sections/examples.png" class="section"/> Skin Example

```yaml
# $HOME/.k9s-alpha/contexts/fred/skins.yml
k9s:
  # General K9s𝞪 styles
  body:
    fgColor: dodgerblue
    bgColor: '#ffffff'
    logoColor: '#0000ff'

  # ClusterInfoView styles
  info:
    fgColor: lightskyblue
    sectionColor: steelblue

  # Frame styles
  frame:
    # Borders styles
    border:
      fgColor: dodgerblue
      focusColor: aliceblue

    # MenuView attributes and styles
    menu:
      fgColor: darkblue
      keyColor: cornflowerblue
      # Used for favorite namespaces
      numKeyColor: cadetblue

    # CrumbView attributes for history navigation.
    crumbs:
      fgColor: white
      bgColor: steelblue
      activeColor: skyblue

    # Resource status and update styles
    status:
      newColor: '#00ff00'
      modifyColor: powderblue
      addColor: lightskyblue
      errorColor: indianred
      highlightcolor: royalblue
      killColor: slategray
      completedColor: gray

    # Border title styles.
    title:
      fgColor: aqua
      bgColor: white
      highlightColor: skyblue
      counterColor: slateblue
      filterColor: slategray

  # Specific views styles
  views:
    # TableView attributes.
    table:
      fgColor: blue
      bgColor: darkblue
      cursorColor: aqua
      # Header row styles.
      header:
        fgColor: white
        bgColor: darkblue
        sorterColor: orange

    # YAML info styles.
    yaml:
      keyColor: steelblue
      colonColor: blue
      valueColor: royalblue

    # Logs styles.
    logs:
      fgColor: white
      bgColor: black
```

<br/>

---
## <img src="/assets/sections/references.png" class="section"/> Named Color Reference

|----------------------|----------------|------------------|-------------------|-----------------|
| black                | maroon         | green            | olive             | navy            |
| purple               | teal           | silver           | gray              | red             |
| lime                 | yellow         | blue             | fuchsia           | aqua            |
| white                | aliceblue      | antiquewhite     | aquamarine        | azure           |
| beige                | bisque         | blanchedalmond   | blueviolet        | brown           |
| burlywood            | cadetblue      | chartreuse       | chocolate         | coral           |
| cornflowerblue       | cornsilk       | crimson          | darkblue          | darkcyan        |
| darkgoldenrod        | darkgray       | darkgreen        | darkkhaki         | darkmagenta     |
| darkolivegreen       | darkorange     | darkorchid       | darkred           | darksalmon      |
| darkseagreen         | darkslateblue  | darkslategray    | darkturquoise     | darkviolet      |
| deeppink             | deepskyblue    | dimgray          | dodgerblue        | firebrick       |
| floralwhite          | forestgreen    | gainsboro        | ghostwhite        | gold            |
| goldenrod            | greenyellow    | honeydew         | hotpink           | indianred       |
| indigo               | ivory          | khaki            | lavender          | lavenderblush   |
| lawngreen            | lemonchiffon   | lightblue        | lightcoral        | lightcyan       |
| lightgoldenrodyellow | lightgray      | lightgreen       | lightpink         | lightsalmon     |
| lightseagreen        | lightskyblue   | lightslategray   | lightsteelblue    | lightyellow     |
| limegreen            | linen          | mediumaquamarine | mediumblue        | mediumorchid    |
| mediumpurple         | mediumseagreen | mediumslateblue  | mediumspringgreen | mediumturquoise |
| mediumvioletred      | midnightblue   | mintcream        | mistyrose         | moccasin        |
| navajowhite          | oldlace        | olivedrab        | orange            | orangered       |
| orchid               | palegoldenrod  | palegreen        | paleturquoise     | palevioletred   |
| papayawhip           | peachpuff      | peru             | pink              | plum            |
| powderblue           | rebeccapurple  | rosybrown        | royalblue         | saddlebrown     |
| salmon               | sandybrown     | seagreen         | seashell          | sienna          |
| skyblue              | slateblue      | slategray        | snow              | springgreen     |
| steelblue            | tan            | thistle          | tomato            | turquoise       |
| violet               | wheat          | whitesmoke       | yellowgreen       | grey            |
| dimgrey              | darkgrey       | darkslategrey    | lightgrey         | lightslategrey  |
| slategrey            |                |                  |                   |                 |