function removeDiacritics(str) {
    return str.split('').map(char => {
        const code = char.charCodeAt(0);
        if (code >= 768 && code <= 879) {
            return ''; // 组合符号范围
        }
        return char.normalize('NFD').replace(/[\u0300-\u036f]/g, '');
    }).join('');
}

let str = 'āáǎà';
let result = removeDiacritics(str);
console.log(result); // 输出: 'aaaa'

import React, { useEffect, useRef, useState } from 'react';
import { View, TextInput, StyleSheet, Dimensions, Text, ScrollView, Button, Switch } from 'react-native';


const OnResponderMoveExample = () => {
  const [isEnabled, setIsEnabled] = React.useState(false);
  const toggleSwitch = () => setIsEnabled(previousState => !previousState);
  const [params, setParams] = React.useState('')
  const [str, setStr] = React.useState('准备执行')
  return (
    <View    onResponderMove={(event) => {
      setStr('执行完毕')
      setParams(JSON.stringify(event.nativeEvent))
    }}>
      <Text>属性值: {"onResponderMove={(event) => {setStr('执行完毕')}}"}</Text>
      <Text>预期效果:{'点击Switch后：“准备执行”变“成执行完毕”，参数打印打印出参数值'}</Text>
      <Text>实际效果</Text>
      <Switch
   
      onValueChange={toggleSwitch}
       value={isEnabled}
      />
      <Text>{str}</Text>
      <Text>参数打印：</Text>
      <Text>{params}</Text>
    </View>
  );
}

export default OnResponderMoveExample

import React, { memo } from 'react';
import { FlatList, View, Text, StyleSheet } from 'react-native';

const list = [
  // 这里是你的数据列表
  { id: 1, name: 'Gift 1' },
  { id: 2, name: 'Gift 2' },
  // 添加更多的列表项
];

const getGiftId = (item) => item.id.toString(); // 转换为字符串作为 key

const GiftItem = memo(({ giftItem }) => {
  return (
    <View style={styles.giftItemContainer}>
      <Text>{giftItem.name}</Text>
    </View>
  );
});

const MyFlatListDemo = () => {
  return (
    <FlatList
      style={styles.flatList}
      data={list}
      keyExtractor={getGiftId}
      renderItem={({ item }) => <GiftItem giftItem={item} />}
      numColumns={4} // 设置为4列
    />
  );
};

const styles = StyleSheet.create({
  flatList: {
    width: '100%', // 填满整个屏幕宽度
    height: 240,   // 设置 FlatList 的高度
    padding: 0,    // 设置内边距
  },
  giftItemContainer: {
    width: '100%',         // 宽度100%，根据列数来调整
    alignItems: 'center',  // 居中对齐
    justifyContent: 'center', // 居中对齐
    height: 100,           // 每个项的高度
  },
});

export default MyFlatListDemo;




'āáǎà'.normalize("NFD").replace(/[\u0300-\u036f]/g, "")

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




React Native 从 0.59 版本到 0.72.4 版本之间经历了许多重大更新和改进。下面是主要的更新内容：

### 0.60.x (2019年7月)
1. **Auto-linking for Native Modules**: 自动链接原生模块，简化了原生模块的配置。
2. **Android X 支持**: React Native 完全迁移到 Android X，开发者需要更新依赖。
3. **新的`useWindowDimensions` Hook**: 更简便的方式来监听窗口尺寸的变化。
4. **CocoaPods 成为默认管理方式**: iOS 项目使用 CocoaPods 作为默认的依赖管理工具。

### 0.61.x (2019年9月)
1. **Fast Refresh**: 引入了 Fast Refresh，结合了“live reloading”和“hot reloading”的优势，提升了开发体验。
2. **修复了多个性能问题**：如在开发者模式下的性能问题。

### 0.62.x (2020年3月)
1. **Flipper 集成**: Flipper 成为默认的 React Native 调试工具，提供了一个现代化的调试界面。
2. **新版 LogBox**: 改进了错误和警告信息的显示，提供了更清晰的调试信息。
3. **引入新的 `useColorScheme` Hook**: 用于检测系统的外观模式（如浅色或深色模式）。

### 0.63.x (2020年7月)
1. **Pressable 组件**: 新的 `Pressable` 组件用于替代 `Touchable` 系列组件，提供了更灵活的触摸事件处理。
2. **默认启用 LogBox**: LogBox 成为默认的错误和警告处理机制。
3. **TextInput Placeholder 文本样式支持**：新增了对 `TextInput` 组件的 `placeholderTextColor` 和 `placeholderTextStyle` 属性的支持。

### 0.64.x (2021年3月)
1. **Hermes 引擎支持 iOS**: Hermes 引擎支持 iOS 平台，优化了应用的启动时间和内存使用。
2. **TypeScript 支持**: 默认模板中加入了 TypeScript 支持，进一步优化了开发体验。
3. **性能改进**：包括减少线程间通信开销等，提升了整体应用性能。

### 0.65.x (2021年8月)
1. **支持新的 Apple Silicon 架构**：优化了对 M1 芯片 Mac 的支持。
2. **ES Modules 支持**：更好地支持 ES 模块导入。
3. **改进内存管理**：特别是在 Android 平台上，通过减少内存泄漏，提升了内存使用效率。

### 0.66.x (2021年10月)
1. **更多 Hermes 引擎改进**：进一步优化 Hermes 的性能表现。
2. **改进的 Gesture Responder System**：提高了触摸事件的响应和处理性能。

### 0.67.x (2022年2月)
1. **性能优化**：包括内存管理和启动时间优化。
2. **引入新的开发者工具**：如改进的调试工具和性能分析工具。

### 0.68.x (2022年5月)
1. **Metro 构建系统改进**：大幅改进了 Metro 构建系统的性能和配置能力。
2. **RN CLI 更新**：React Native CLI 获得了许多改进和新特性。

### 0.69.x (2022年8月)
1. **React 18 支持**: 完全支持 React 18，包括 `Concurrent Mode` 和 `Suspense` 的功能。
2. **Fabric 及 TurboModules 的初步集成**: 开启了新架构的初步支持，包括 Fabric 和 TurboModules 的实验性功能。

### 0.70.x (2022年12月)
1. **Hermes 成为默认 JS 引擎**: Hermes 现在是默认的 JavaScript 引擎，这为大多数应用带来了性能上的提升。
2. **支持 ESLint 8.x**: 更新了 ESLint 版本，并增强了静态代码分析能力。
3. **稳定的 Fabric 支持**: Fabric 渲染器和 TurboModules 进一步稳定，逐步推广使用。

### 0.71.x (2023年3月)
1. **Hermes 版本更新**: 新的 Hermes 版本带来了更多的性能改进和错误修复。
2. **新架构的全面支持**: React Native 新架构（包括 Fabric 和 TurboModules）开始全面推广，提供了更高的性能和更强的扩展能力。
3. **多线程支持**: 新架构中，进一步改进了多线程支持，增强了应用在高并发场景下的表现。

### 0.72.x (2023年7月)
1. **Metro Bundler 更新**: Metro 继续优化，支持更多的 ES 特性和更高效的打包流程。
2. **Jest 和 Testing Library 支持**: 默认支持新的测试工具，更加简便地进行单元测试和集成测试。
3. **新的 Debugger**: 引入了新的调试工具，增强了开发过程中的调试能力，特别是与 Flipper 的集成。
4. **新架构完善**: Fabric 渲染器和 TurboModules 的功能进一步完善，并开始推广为生产环境的默认选项。

这些版本之间的更新，不仅引入了大量的新特性和性能改进，还推动了 React Native 的发展，特别是对 Hermes 引擎、新架构（Fabric 和 TurboModules）的支持和推广。开发者在升级时应注意各版本的迁移指南，确保平稳过渡。
