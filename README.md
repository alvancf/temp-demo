RNOH doesn't hijack imports when importing stuff from react-native internals.
﻿
import {Image} from 'react-native'
// ...
Image.resolveAssetSource(uri)
