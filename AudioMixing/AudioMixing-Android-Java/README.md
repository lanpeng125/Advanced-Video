# AudioMixing-Android-Java

这个开源示例项目演示了如何快速集成 网易云信 新一代（G2）音视频 SDK，实现通话过程中混音效果功能。

## 环境准备，运行示例项目，多人视频通话功能实现

这个开源示例项目基于多人视频通话，关于**环境准备**，**运行示例项目**，**功能实现**章节请参考[README.md](https://github.com/netease-im/Basic-Video-Call/blob/master/Group-Video/NERtcSample-GroupVideoCall-Android-Java/README.md)
## 功能实现

如果需要实现混音音效，参考如下步骤，在你的项目中实现播放混音文件：

1. 在加入频道成功后调用 startAudioMixing 开始混音。
2. 根据 pauseAudioMixing、resumeAudioMixing 等操作 进行 暂停、恢复、控制音量、定位 等功能。
3. 在离开频道前调用 stopAudioMixing 结束混音。
<br>**目前只支持SD卡上的本地文件路径。**

## 示例代码

### 混音(Mixing)效果实现：
```java
NERtcCreateAudioMixingOption option = new NERtcCreateAudioMixingOption();
option.path = musicPathArray[musicIndex];
option.playbackVolume = audioMixingVolume;
option.sendVolume = audioMixingVolume;
option.loopCount = 1;
result = NERtcEx.getInstance().startAudioMixing(option);
```

### 音效(Effect)实现
```java
NERtcCreateAudioEffectOption option = new NERtcCreateAudioEffectOption();
option.path = effectPathArray[index];
option.playbackVolume = audioEffectVolume;
option.sendVolume = audioEffectVolume;
option.loopCount = 1;
neRtcEx.stopEffect(index2Id(index));
return neRtcEx.playEffect(index2Id(index),option) == 0;
```

## 混音（Mixing）与音效(Effect)区别
混音同一时刻只能播放一首音乐，音效可以播放多首，并设置不同的Id管理。
详细使用请见[混音音效](https://dev.yunxin.163.com/docs/product/%E9%9F%B3%E8%A7%86%E9%A2%91%E9%80%9A%E8%AF%9DG2/SDK%E5%BC%80%E5%8F%91%E9%9B%86%E6%88%90/Android%E5%BC%80%E5%8F%91%E9%9B%86%E6%88%90/%E6%B7%B7%E9%9F%B3%E9%9F%B3%E6%95%88)



