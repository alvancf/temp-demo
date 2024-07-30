https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1190  (platformcolor)

https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1131     flexDirection is set to "row-reverse,"
https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1099  axios传中文的问题  close
https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1167 RNViewBase居中的问题  close
https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1113   ClipPathView问题

Expected effect: Two fingers can control image zooming, a feature that works normally on both Android and iOS. In the HarmonyOS RN framework, the parameters passed into the two-finger callback function do not match the time-triggered parameters used in the source code for judgment, rendering the two-finger events ineffective.

Harmony In the RN framework, the input parameter of the two-finger callback function is inconsistent with that in the source code.

// app.js
import React from 'react'
import {
StyleSheet,
SafeAreaView,
ScrollView,
Image,
Dimensions,
} from 'react-native'
import ImageZoom from '@react-native-oh-tpl/react-native-image-pan-zoom'

const styles = StyleSheet.create({
// 最外层容器样式
mainContainer: {
flex: 1,
},
debugButton: {
marginBottom: 10,
paddingTop: 20,
paddingBottom: 20,
backgroundColor: '#68a0cf',
borderWidth: 1,
borderColor: '#fff',
},
debugButtonText: {
color: '#fff',
textAlign: 'center',
},
})

const BridgeDebugApp: React.FC = () => (
<SafeAreaView style={styles.mainContainer} removeClippedSubviews={false}>
<ScrollView style={{ paddingTop: 20, paddingHorizontal: 16 }}>
<ImageZoom
cropWidth={Dimensions.get('window').width}
cropHeight={Dimensions.get('window').height}
imageWidth={200}
imageHeight={200}
>
<Image
style={{ width: 200, height: 200 }}
source={{ uri: 'https://picasso-static.xiaohongshu.com/fe-platform/546b214eb6a0b69f921bacd1c907422ab2bf3c2a.png' }}
/>
</ImageZoom>
</ScrollView>
</SafeAreaView>
)

export default BridgeDebugApp
