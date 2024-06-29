Hello,If the KeyboardAvoidingView component contains the ScrollView component, the display effect is incorrect.
When the behavior attribute of the KeyboardAvoidingView component is set to {"padding"} or {"height"}, 
if the input box is at the bottom of the ScrollView list, the input box does not move up when the keyboard pops up.
If the input box is in the middle of the ScrollView list and near the bottom of the screen, 
the input box can be moved up when the keyboard pops up. However, the moved input is not close to the keyboard, and there is a blank space between the input box and the keyboard.

demo：import {
  KeyboardAvoidingView,
  TextInput,
  View,
  ScrollView
} from "react-native";
import * as React from "react";

const App = () => {
  return (
    <>
      <ScreenComponent />
    </>
  );
};

const ScreenComponent = () => {
  return (
    <View style={{ flex: 1, backgroundColor: "red" }}>
      <KeyboardAvoidingView 
        style={{ height: "100%", width: "100%", backgroundColor: "pink" }}
        behavior={"padding"}
      >
        <ScrollView style={{}} indicatorStyle = 'black'>
          <View style={{ width: 100, height: 100, backgroundColor: "red" }}></View>
          <TextInput
            value={"I am in the top of the input box"}
            style={{ height: 50, width: 200, backgroundColor: "orange" }}
          />
          <View style={{ width: 100, height: 100, backgroundColor: "blue" }}></View>
          <View style={{ width: 100, height: 100, backgroundColor: "yellow"}}></View>
          <View style={{ width: 100, height: 100, backgroundColor: "blue" }}></View>
          <View style={{ width: 100, height: 100, backgroundColor: "purple" }}></View>
          <View style={{ width: 100, height: 100, backgroundColor: "red" }}></View>
          <View style={{ width: 100, height: 100, backgroundColor: "red" }}></View>
          <View style={{ width: 100, height: 100, backgroundColor: "red" }}></View>
          <TextInput
            value={"I am in the middle of the input box"}
            style={{ height: 50, width: 200, backgroundColor: "orange" }}
          />
          <View style={{ width: 100, height: 100, backgroundColor: "red" }}></View>
          <View style={{ width: 100, height: 100, backgroundColor: "blue" }}></View>
          <View style={{ width: 100, height: 100, backgroundColor: "yellow"}}></View>
          <View style={{ width: 100, height: 100, backgroundColor: "red" }}></View>
          <View style={{ width: 100, height: 100, backgroundColor: "blue" }}></View>
          <View style={{ width: 100, height: 100, backgroundColor: "yellow"}}></View>
          <TextInput
            value={"I am in the bottom of the input box"}
            style={{ height: 50, width: 200, backgroundColor: "orange" }}
          />
        </ScrollView>
      </KeyboardAvoidingView>
    </View>
  );
};

export default App;


In rn, when the View flexDirection is set to "row-reverse," margin-right is displayed as the visual left on iOS, while Harmony is the visual right.

<View style={{ backgroundColor: "grey", width: 300, marginLeft: 20 }}>
<View
style={{
width: 260,
// marginRight: 20,
marginEnd: 20,
backgroundColor: "green",
flexDirection: "row-reverse"
}}>
<View
style={{
width: 40,
height: 40,
backgroundColor: "red"
}}
/>
</View>
</View>
