---
title: Using SVGs with React Native
sidebar_title: Using SVGs
---

import SnackInline from '~/components/plugins/SnackInline';
import TerminalBlock from '~/components/plugins/TerminalBlock';

SVGs (Scalable Vector Graphics) are a great way to present icons and other visual elements in a flexible, crisp, performant way. Using SVGs on the web is straightforward, since we can copy an SVG and place it inline in an HTML file, and it will work. This is because browsers understand how to parse and present SVG. React Native does not understand how to parse and present SVG out of the box, so we'll need to use a package and an SVG converter to do so.

Let's go over the whole process of creating an SVG to presenting it in React Native.

## Exporting an SVG

Once we have a vector design inside a design program, like Figma, Illustrator, or Sketch, we can find the "export" menu, and specify "SVG" as the type of exported file. Alternatively, these programs often allow right clicking on an element, then copying it as an SVG.

## Converting an SVG for React Native

Next, let's convert our SVG to be compatible with React Native. [React-SVGR](https://react-svgr.com/playground/?native=true) is a great tool to accomplish this. It takes an SVG as input then transforms them into other formats, including one that works with React Native.

We can paste the SVG contents from our exported SVG file into [React-SVGR](https://react-svgr.com/playground/?native=true), and it will provide output so that we can copy and paste into our React Native project.

To automate this process, React-SVGR also [provides a CLI](https://react-svgr.com/docs/cli/) that could allow us to put regular SVGs in our project, then run a script that would convert them into React Native components automatically.

## Including the SVG in our project

Once we have a compatible SVG, we'll need to add [react-native-svg](https://github.com/react-native-svg/react-native-svg) to our project. You can do so with:

<TerminalBlock cmd={['expo install react-native-svg']} />

Then we can add code like the following to our project:

<SnackInline dependencies={['react-native-svg']}>

<!-- prettier-ignore -->
```jsx
import React from 'react';
import { Text, View, StyleSheet } from 'react-native';
import Svg, { Path } from "react-native-svg"

export default function ChevronDown() {
  return (
    <View style={styles.container}>
      <Svg
      width={20}
      height={20}
      viewBox="0 0 20 20"
      >
        <Path d="M16.993 6.667H3.227l6.883 6.883 6.883-6.883z" fill="#000" />
      </Svg>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
  },
});

```

</SnackInline>
