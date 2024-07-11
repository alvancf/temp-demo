RN桥接原生的一个空白view，在RN页面上显示位置不对，如果它作为第一个叶子节点，那么就是屏幕内居中的（不正常），如果不是第一个叶子节点，就按顺序排在后面（正常）

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
