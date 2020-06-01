# PPT

## 怎么在场景中插入 ppt

### 场景操作的核心方法

相当于日常电脑操作的 “另存成”, 就是将场景存入对应的地址中。

```javascript
room.putScenes(`/init`, scenes); // 插入 ppt 内容
```

相当于日常电脑操作的 “打开文件夹”, 就是到指定的地址访问对应的场景。

```javascript
room.setScenePath(`/init/page2`); // 显示相应的内容为：init 下的第二页
```

### 临时提交文档转换服务的处理方法

```javascript
import {Room, PptConverter} from "white-web-sdk";
const pptConverter = whiteWebSdk.pptConverter(roomToken);
res = await pptConverter.convert({
        url: pptURL, // 源文件地址
        kind: kind, // 转码类型
        onProgressUpdated: progress => {
            console.log(progress) // 转码进度
        },
    });

// convert 方法是输入一个文档地址，返回一个场景数组 [Scene, Scene, Scene]
room.putScenes(`/init`, res.scenes);
room.setScenePath(`/init/page2`);
```

### 从服务器获取的数据的处理方法

```javascript
// [url, url] 或者 [json, json] 经过 map 处理后互动
const scenes: []Scene = [url, url].map()

// convert 方法是输入一个文档地址，返回一个场景数组 [Scene, Scene, Scene]
room.putScenes(`/`, scenes);
room.setScenePath(`/init/page2`);
```

## 怎么切换 ppt

```javascript
 // 上一步
 room.pptPreviousStep();
 // 下一步
 room.pptNextStep();
 // 切换到指定的 path
 room.setScenePath(`/init/page2`);
 // 此方法如果在动态 ppt 中，那么就是下一个动画。如果在静态 ppt 中，那么就是下一页
```

