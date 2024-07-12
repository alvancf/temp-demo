RN桥接原生的一个空白view，在RN页面上显示位置不对，如果它作为第一个叶子节点，那么就是屏幕内上下方向居中的（不正常），如果不是第一个叶子节点，就按顺序排在后面（正常）

在rn中使用一个自定义组件，自定义组件是使用RNViewBase构建的，当这个自定义组件在rn代码作为第一个叶子节点时，它会在屏幕内上下居中显示，如果不是第一个叶子节点，就可以按照顺序从上往下排列布局

自定义组件的代码片段： build() {
  RNViewBase({ctx: this.ctx, tag: this.tag}) {
    // 任意元素
  }
}  

rn代码片段： render() {
  return (
    <View style={{flex: 1, backgroundColor: #fff}}>
      // 自定义组件
    </View>
  )
}


操作步骤：这个三方库直接npm i 即可。点击按钮，弹窗的上面白色横杠区域是可以拖动的，拖动松开，高度会弹开，鸿蒙整个过程相对其他平台环境卡顿明显，如果未复现，麻烦多次试下拖动和松开拖动我想知道这是rnoh性能问题还是其他方面的问题？如果是rnoh的问题，麻烦列入issue list进行修复。
，还有个问题是，如果我们拖动哪个白色横杠只拖动一点点,那么高度会弹回到初始位置,这样我们点击下面的任何表情包都将无效，就是点击不到，

import React from 'react';
import {StyleSheet, Button, Text} from 'react-native';
import EmojiPicker, {type EmojiType} from 'rn-emoji-keyboard';

export default function () {
  const [result, setResult] = React.useState<string>();
  const [isOpen, setIsOpen] = React.useState<boolean>(false);

  const handlePick = (e: EmojiType) => {
    setResult(e.emoji);
    console.log('Emoji!!!!!:', JSON.stringify(e));
  };

  return (
    <>
      <Text style={styles.textIcon}>{result || ' '}</Text>
      <Button onPress={() => setIsOpen(true)} title="open:basic" />
      <EmojiPicker
        onEmojiSelected={handlePick}
        open={isOpen}
        onClose={() => setIsOpen(false)}
      />
    </>
  );
}

const styles = StyleSheet.create({
  textIcon: {
    marginHorizontal: 16,
    marginVertical: 32,
    textAlign: 'center',
    fontSize: 42,
    color: '#000',
  },
});
