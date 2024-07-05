在鸿蒙中，当我们使用fetch获取本地svg图片信息时，metro热加载的方式可以正常获取，但是打包到bundle就获取不到，其他系统是可以正常获取到的

In Harmony, when fetch is used to obtain the local svg image information, metro hot loading can be obtained.

import React, {useEffect, useState, Component} from 'react';
import {
  View,
  Text,
  StyleSheet,
  ScrollView,
  SafeAreaView,
  Image,
} from 'react-native';
import resolveAssetSource from 'react-native/Libraries/Image/resolveAssetSource';

export default function () {
  const [svgText, setSvgText] = useState('');
  // 本地svg文件的路径
  const uri = require('./1.svg');
  const source = resolveAssetSource(uri);
  fetch(source.uri)
    .then(response => {
      if (!response.ok) {
        throw new Error(`fetch error! status: ${response.status}`);
      }
      return response.text();
    })
    .then(svgText => {
      console.log(`fetch local svg file: ${svgText}`);
      setSvgText(svgText);
    })
    .catch(error => {
      console.error(
        'There has been a problem with your fetch operation:',
        error,
      );
    });

  return (
    <SafeAreaView style={styles.container}>
      <ScrollView>
        <Image
          style={styles.tinyLogo}
          source={require('../../../assets/1.svg')}
        />
        <Image
          style={styles.tinyLogo}
          source={{
            uri: 'https://reactnative.dev/img/tiny_logo.png',
          }}
        />
        <Text style={styles.label}>Local SVG XML uri:</Text>
        <Text style={styles.text}>{source.uri}</Text>
        <Text style={styles.label}>Local SVG XML content:</Text>
        <Text style={styles.text}>{svgText}</Text>
      </ScrollView>
    </SafeAreaView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    marginTop: 20,
    padding: 20,
  },
  section: {
    marginBottom: 20,
  },
  label: {
    fontSize: 16,
    fontWeight: 'bold',
  },
  text: {
    lineHeight: 24,
  },
  tinyLogo: {
    width: 50,
    height: 50,
  },
});
