# yy-video-player
基于uni-app开发的一款视频播放器插件，开箱即用，具有视频下载，页面返回，弹幕，进度条等功能。
# 使用截图
## 非全屏待播放
<img src="http://tva1.sinaimg.cn/large/007X8olVly1g7wvuhud80j30u01o0n4v.jpg" width=250>

## 全屏播放
<img src="http://tva1.sinaimg.cn/large/007X8olVly1g7wvukmml1j31o00u04fz.jpg" width=550>

## 使用教程
导入插件
  ```JavaScript
    import yyVideoPlayer from '@/components/yy-video-player.nvue';
  ```
声明插件
  ```JavaScript
    components: {
        yyVideoPlayer
    }
  ```
使用插件
  ```JavaScript
  <yy-video-player 
    :auto-play="false" 
    :url="url"  
    :poster="poster" 
    :danmu-list="danmuList"  
    :show-back-btn="true"
  ></yy-video-player>
  ```
参数说明：

| 属性 | 说明 | 是否必填 | 默认值 |
| ------ | ------ | ------ | ------ |
| url | 视频地址，支持的格式请参考uni-app官网  | 是 |  |
| poster | 视频封面地址，支持的格式请参考uni-app官网  | 是 |  |
| auto-play | 是否自动播放 | 否 | true |
| danmu-list | 弹幕列表  | 否 | [] |
| show-back-btn | 是否显示返回按钮  | 否 | false |
| show-download-btn | 是否显示下载按钮  | 否 | false |
| process-bar-color | 进度条颜色  | 否 | #39BFFD |

## 其它说明
  如需设置后台不播放，返回页面继续播放，请在使用插件的页面内监听：
  
  ```JavaScript
      onShow() {
        if (this.videoContext) {
          this.videoContext.play();
         }
      },
      onReady: function() {
       this.videoContext = uni.createVideoContext('video', this);
      },
      onHide: function() {
        if (this.videoContext) {
          this.videoContext.stop();
        }
      }
  ```
## 发弹幕使用

  ```JavaScript
    this.videoContext.sendDanmu({
      text: this.danmuValue,
      color: "#FFF"
    });
  ```

## 本人很菜，如有bug欢迎提issue。
