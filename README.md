这个问题帮忙请教波兰人：

按照下面的测试案例，ScrollView中设置View及Text的样式，部分item的borderBottom不显示。

According to the following test case, when the View and Text styles are set in ScrollView, the borderBottom of some items is not displayed.

测试案例：
import { StyleSheet, Text, View, ScrollView } from 'react-native';

const App = () => {
  const renderContent = () => {
    const items = Array.from({ length: 100 }, (_, i) => `Item ${i + 1}`);
    return (
      <View>
        {items.map((item, index) => (
          <View style = {styles.item}>
            <Text key={index} style={styles.text}>
              {item}
            </Text>
          </View>
        ))}
      </View>
    );
  };

  return (
    <ScrollView>
      {renderContent()}
    </ScrollView>
  );
}
const styles = StyleSheet.create({
  item: {
    borderBottomWidth: 0.3,
    backgroundColor: '#fff',
  },
  text: {
    fontSize: 15,
    marginTop: 9
  },
});

export default App;


