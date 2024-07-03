https://gl.swmansion.com/rnoh/react-native-harmony/-/issues/1131

import * as React from 'react';
import {Animated, FlatList, ViewStyle, StyleProp, View} from 'react-native';
// import FastImage from 'react-native-fast-image';

const AnimatedFlatList = Animated.createAnimatedComponent(FlatList);
const unit = 380 / 750;
const unitHeight = 830 / 1624;

interface ImageData {
  bg: string;
  dybg: string;
}

export const PDFDemo = React.memo((props: {}) => {
  const datas: ImageData[] = [
    {
      bg: 'https://ucmp-static.sf-express.com/sfoss/ad-act/gift-Delivery-card/26AD04CAD15645B3A33F732DD07889A0.png',
      dybg: 'https://ucmp-static.sf-express.com/sfoss/ad-act/gift-Delivery-card/83B6816B38834136AE11331B68787CBF.gif',
    },
    {
      bg: 'https://ucmp-static.sf-express.com/sfoss/ad-act/gift-Delivery-card/4D1D07E3FCCA48BDBCA54FD7846481BF.jpg',
      dybg: 'https://ucmp-static.sf-express.com/sfoss/ad-act/gift-Delivery-card/23CEE18EEA7944958639431DF3CFDB18.gif',
    },
    {
      bg: 'https://ucmp-static.sf-express.com/sfoss/ad-act/gift-Delivery-card/30DFC78CF11C49B18A61E0BFB1482A95.jpg',
      dybg: 'https://ucmp-static.sf-express.com/sfoss/ad-act/gift-Delivery-card/D1AF84E7A81046A09E682AE4E607E750.gif',
    },
    {
      bg: 'https://ucmp-static.sf-express.com/sfoss/ad-act/gift-Delivery-card/62A2031EA1354A25A21A6078646273F4.png',
      dybg: 'https://ucmp-static.sf-express.com/sfoss/ad-act/gift-Delivery-card/5A52A4797CDE42F29A4DD0C4E2EF19A4.gif',
    },
    {
      bg: 'https://ucmp-static.sf-express.com/sfoss/ad-act/gift-Delivery-card/53356E47C948485785805BA7BC2AD3DF.png',
      dybg: 'https://ucmp-static.sf-express.com/sfoss/ad-act/gift-Delivery-card/EEE0BEC36E244A7C9569547AAA810EB7.gif',
    },
    {
      bg: 'https://ucmp-static.sf-express.com/sfoss/ad-act/gift-Delivery-card/F5FEF4BD8A8749E794274967BDAFD3E1.jpg',
      dybg: 'https://ucmp-static.sf-express.com/sfoss/ad-act/gift-Delivery-card/6F22774069E44F388819188315577B52.gif',
    },
    {
      bg: 'https://ucmp-static.sf-express.com/sfoss/ad-act/gift-Delivery-card/C948D1850EBF4F089C59F300D2EA6F09.jpg',
      dybg: 'https://ucmp-static.sf-express.com/sfoss/ad-act/gift-Delivery-card/499A35E7577342A89B5A8E45F34A8B7B.gif',
    },
    {
      bg: 'https://ucmp-static.sf-express.com/sfoss/ad-act/gift-Delivery-card/E38A572030A840CDA57E43042A42F053.jpg',
      dybg: 'https://ucmp-static.sf-express.com/sfoss/ad-act/gift-Delivery-card/25A080C789BF46F9A93517730296AF93.gif',
    },
  ];

  const listSize = datas.length;
  const [selectIndex, setSelectIndex] = React.useState<number>(0);
  let tempSelectIndex: number = selectIndex;
  const scrollX: Animated.Value = React.useRef(new Animated.Value(0)).current;
  const flatRef = React.useRef<FlatList>(null);

  React.useEffect(() => {
    const onToIndex = (event: {selectIndex: number}) => {
      if (flatRef) {
        flatRef.current?.scrollToIndex({index: event.selectIndex});
      }
    };
    // const listener = DeviceEventEmitter.addListener(
    //   changeSelectIndexToBig,
    //   onToIndex
    // );
    // return () => {
    //   listener.remove();
    // };
  }, []);
  // 当用户没有在滑动时，lastEndDragIndex这个值和props.selectIndex是相等的。
  const [lastEndDragIndex, setLastEndDragIndex] = React.useState(selectIndex);
  const onScrollDragging = React.useRef(false);
  React.useEffect(() => {
    if (!onScrollDragging.current) {
      setLastEndDragIndex(selectIndex);
    }
  }, [selectIndex]);
  const compatUnit = Math.min(unit, unitHeight);
  const realityImgPageWidth = 520 * compatUnit;
  const realityImgPageHeight = 780 * compatUnit;
  const editBlessBtnHeight = 52 * compatUnit;
  const blessDialogHeight = 530 * unitHeight + 34;
  const dialogModeMiddleHeight = 830 - 44 - 44 - blessDialogHeight;
  const dialogModeMarginTop =
    (dialogModeMiddleHeight - realityImgPageHeight - editBlessBtnHeight) / 2;

  return (
    <View style={{flex: 1, justifyContent: 'center', alignItems: 'center'}}>
      <AnimatedFlatList
        style={{
          height: realityImgPageHeight + editBlessBtnHeight,
          width: realityImgPageWidth,
          overflow: 'visible',
        }}
        ref={flatRef}
        data={datas}
        renderItem={itemData => {
          return (
            <ListItemBigView
              item={itemData.item as ImageData}
              signName={'signName'}
              index={itemData.index}
              isShowDynamicPic={itemData.index === lastEndDragIndex}
              itemWidth={realityImgPageWidth}
              itemHeight={realityImgPageHeight}
              editBlessBtnHeight={editBlessBtnHeight}
              isDialogMode={false}
              scrollX={scrollX}
              onClickEditBlessBtn={() => {}}
            />
          );
        }}
        getItemLayout={(param, index) => ({
          length: realityImgPageWidth,
          offset: realityImgPageWidth * index,
          index,
        })}
        horizontal={true}
        keyExtractor={(item: any, index: number) => {
          return `big${index}${item.cardId}`;
        }}
        initialScrollIndex={selectIndex}
        pagingEnabled={true}
        removeClippedSubviews={false}
        showsHorizontalScrollIndicator={false}
        onScroll={Animated.event(
          [
            {
              nativeEvent: {
                contentOffset: {
                  x: scrollX,
                },
              },
            },
          ],
          {
            useNativeDriver: true,
            listener: (event: any) => {
              const x = event.nativeEvent.contentOffset.x;
              // 当前展示位置
              const currentIndex = Math.round(x / realityImgPageWidth);
              if (
                currentIndex !== tempSelectIndex &&
                currentIndex > -1 &&
                currentIndex < datas.length
              ) {
                tempSelectIndex = currentIndex;
                setSelectIndex(currentIndex);
              }
            },
          },
        )}
        onScrollBeginDrag={event => {
          tempSelectIndex = selectIndex;
          onScrollDragging.current = true;
        }}
        onScrollEndDrag={() => {
          setLastEndDragIndex(tempSelectIndex);
          onScrollDragging.current = false;
        }}
      />
    </View>
  );
});

interface IListItemBigViewProps {
  item: ImageData;
  index: number;
  itemWidth: number;
  itemHeight: number;
  /** 编辑祝福语按钮高度 */
  editBlessBtnHeight: number;
  style?: StyleProp<ViewStyle>;
  scrollX: Animated.Value;
  onClickEditBlessBtn: () => void;
  /** 署名名称 */
  signName: string;
  isDialogMode: boolean;
  isShowDynamicPic: boolean;
}

const ListItemBigView = (props: IListItemBigViewProps) => {
  const {item, index, itemWidth, itemHeight, scrollX, editBlessBtnHeight} =
    props;
  const dynamicPic = item.dybg;
  const backgroundPic = item.bg;
  let cardBless = 'blessMsg';

  const imgWidth = itemWidth;
  const imgHeight = itemHeight;
  const position = index * itemWidth;
  const positionBegin = position - itemWidth;
  const positionEnd = position + itemWidth;

  const scaleInterpolate = scrollX.interpolate({
    inputRange: [positionBegin, position, positionEnd],
    outputRange: [0.75, 1, 0.75],
    extrapolate: 'clamp',
  });

  const opacityInterpolate = scrollX.interpolate({
    inputRange: [positionBegin, position, positionEnd],
    outputRange: [0.3, 1, 0.3],
    extrapolate: 'clamp',
  });

  const showEditBless = true;
  const unitCompat = Math.min(unit, unitHeight);
  return (
    <Animated.View
      style={[
        {
          width: itemWidth,
          height: itemHeight + editBlessBtnHeight,
          opacity: opacityInterpolate,
          transform: [{scale: scaleInterpolate}],
          alignItems: 'center',
          justifyContent: 'center',
        },
      ]}>
      <Image
        source={{
          uri: backgroundPic,
        }}
        style={[
          {
            width: imgWidth,
            height: imgHeight,
            borderRadius: 14 * unitCompat,
            overflow: 'hidden',
          },
        ]}
      />
      {props.isShowDynamicPic ? (
        <Image
          source={{
            uri: dynamicPic,
          }}
          style={{
            position: 'absolute',
            top: 0,
            left: 0,
            width: imgWidth,
            height: imgHeight,
          }}
        />
      ) : null}
    </Animated.View>
  );
};
