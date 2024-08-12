import { Tester, TestSuite, TestCase } from '@rnoh/testerino';
import React, { useEffect, useRef, useState } from 'react';
import { View, TextInput, StyleSheet, Dimensions, Text, ScrollView } from 'react-native';


function BugMeasureDemo() {
    
    const viewRef = useRef<View | null>(null);
    
    const [pageH, setpageH] = useState(0);
    
    const [measurePageY, setmeasurePageY] = useState(0);
    
    useEffect(() => {
        setpageH( Dimensions.get('window').height);
        const tid = setInterval(getPageY, 1000);
        return () => {
            clearInterval(tid);
        }
    }, []);
    
    const getPageY = () => {
        viewRef.current?.measure((x, y, width, height, pageX, pageY) => {
            setmeasurePageY(pageY);
        });
    } 
    
    return (
        <>
            <ScrollView>
            <Tester>
                <TestSuite name='Measure Bug'>
                    {
                        Array.from({length: 12}).map((_, i) => 
                        <TestCase key={i} itShould={`TextInput ${i}`}>
                            <TextInput style={styles.inp} />
                        </TestCase>
                        )
                    }
                    <TestCase itShould={`点击输入框键盘弹起，计算的PageY发生错误`}>
                        <Text>windowHeight: {pageH}</Text>
                        <Text>PageY: {measurePageY}</Text>
                        <View ref={viewRef}>
                            <TextInput style={[styles.inp, {borderColor: '#000'}]} />
                        </View>
                    </TestCase>
                </TestSuite>
            </Tester>
            </ScrollView>
        </>
    )
}

const styles = StyleSheet.create({
    inp: {
        height: 36,
        borderWidth: 1,
        borderColor: '#f0f0f0',
        borderRadius: 6
    }
})

export default BugMeasureDemo

https://gl.swmansion.com/rnoh/react-native-harmony/-/merge_requests/1439)
https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1190  (platformcolor)  Rafał Moneta
IDE：5.0.3.500
SDK：HarmonyOS NEXT Developer Beta2  5.0.0.31
晚上我用这个方法验证没啥问题，传入了错的ID，ID在color.json中没有的时候才返回了这个错

https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1131     flexDirection is set to "row-reverse,"
https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1099  axios传中文的问题  close
https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1167 RNViewBase居中的问题  close
https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1113   ClipPathView问题

https://github.com/ascoders/react-native-image-zoom/blob/master/src/image-zoom/image-zoom.component.tsx
    onMoveShouldSetPanResponder: this.props.onMoveShouldSetPanResponder,
    onPanResponderTerminationRequest


这个问题,还没解决。
response data {"code": "2000000", "count": 0, "productId": "ä¸­æ", "questionStatus": 0, "questionType": "c2b", "success": true, "topQuestions": []} 200   
response data {"code": "2000000", "count": 0, "productId": "中文", "questionStatus": 0, "questionType": "c2b", "success": true, "topQuestions": []} 200 

效果不一致
import React, {useEffect, useState} from 'react';
import {Text, View} from 'react-native';
import axios from 'axios';

const url =
  'https://openapi.vmall.com/ccs/question/queryQuestionOverview?productId=中文&_becode=CN&displayUnPublic=false&displayTopQuestion=true';

const str = encodeURIComponent('中文');
const url2 = `https://openapi.vmall.com/ccs/question/queryQuestionOverview?productId=${str}&_becode=CN&displayUnPublic=false&displayTopQuestion=true`;

function App(): JSX.Element {
  const [selectedIndex, setSelectedIndex] = useState('ccc');
  const [selectedIndex2, setSelectedIndex2] = useState('ccc2');
  useEffect(() => {
    const asyncFun = async () => {
      try {
        const response = await axios.get(url);
        console.log('response data', response.data, response.status);
        setSelectedIndex(response.data.productId);
        const response2 = await axios.get(url2);
        console.log('response2 data', response2.data, response2.status);
        setSelectedIndex2(response2.data.productId);
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
      <Text>{selectedIndex}</Text>
      <Text>{selectedIndex2}</Text>
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
