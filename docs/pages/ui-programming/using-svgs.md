---
title: Using SVGs with React Native
sidebar_title: Using SVGs
---

import SnackInline from '~/components/plugins/SnackInline';
import TerminalBlock from '~/components/plugins/TerminalBlock';

SVGs (Scalable Vector Graphics) are a great way to present icons and other visual elements in a flexible, crisp, and performant way. Using SVGs on the web is straightforward, since we can copy an SVG and place it inline in an HTML file. This works because browsers understand how to parse and present SVGs. React Native does not understand how to parse and present SVG out of the box, so we'll need to use a React Native package and an SVG converter to do so.

Let's go over the whole process of creating an SVG to presenting it in a React Native project.

## Exporting an SVG

Once we have a vector created inside a design program, like Figma, Illustrator, or Sketch, find the "export" menu and specify "SVG" as the export type. This will create an SVG file we can view in a code editor. Alternatively, these programs often allow right clicking on an element, then copying it as an SVG.

## Converting an SVG for React Native

Now, it's time to convert our SVG to be compatible with React Native. [React-SVGR](https://react-svgr.com/playground/?native=true) is a great tool to accomplish this. It takes an SVG as input then can transform it into another format, including a format that works with React Native.

Paste the SVG contents from the exported SVG file into [React-SVGR](https://react-svgr.com/playground/?native=true) and make sure the "native" checkbox is ticked. It will provide output that we can copy and paste into our React Native project.

To automate this process, React-SVGR also [provides a CLI](https://react-svgr.com/docs/cli/) that could allow us to put regular SVGs in our project, then run a script that would convert them into React Native components automatically. If you have many icons, or a team of developers working on your project, it's definitely worth the time to set up process like this.

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

You can learn more about SVG with our [API Reference document on SVG](http://localhost:3002/versions/latest/sdk/svg/).
