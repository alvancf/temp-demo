RNOH doesn't hijack imports when importing stuff from react-native internals.
﻿
import {Image} from 'react-native'
// ...
Image.resolveAssetSource(uri)


Image 组件的加载，未优先判断本地缓存图片，而是先 show 一次 defaultSource 图片，然后再加载 source 图片，导致图片闪动现象
