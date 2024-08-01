https://gl.swmansion.com/rnoh/react-native-harmony/-/merge_requests/1439)
https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1190  (platformcolor)

https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1131     flexDirection is set to "row-reverse,"
https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1099  axios传中文的问题  close
https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1167 RNViewBase居中的问题  close
https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1113   ClipPathView问题

这个问题,还没解决。
response data {"code": "2000000", "count": 0, "productId": "ä¸­æ", "questionStatus": 0, "questionType": "c2b", "success": true, "topQuestions": []} 200   
response data {"code": "2000000", "count": 0, "productId": "中文", "questionStatus": 0, "questionType": "c2b", "success": true, "topQuestions": []} 200 

效果不一致
import React, {useEffect} from 'react';
import {Text, View} from 'react-native';
import axios from 'axios';

const url =
  'https://openapi.vmall.com/ccs/question/queryQuestionOverview?productId=中文&_becode=CN&displayUnPublic=false&displayTopQuestion=true';

function App() {
  useEffect(() => {
    const asyncFun = async () => {
      try {
        const response = await axios.get(url);
        console.log('response data', response.data, response.status);
        return response;
      } catch (e) {
        console.error('Error fetching data', e);
        return e;
      }
    };
    asyncFun();
  }, []);

  return (
    <View style={{marginTop: 50}}>
      <Text>Check console logs</Text>
    </View>
  );
}

export default App;

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
