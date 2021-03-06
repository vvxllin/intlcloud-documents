## 功能描述
COS 通过数据万象接口 **imageMogr2** 提供格式转换、gif 格式优化、渐进显示功能。

>图片处理功能为收费项，由数据万象收取，详细的计费说明请参见数据万象 [计费与定价](https://intl.cloud.tencent.com/document/product/1045/33431)。

## 接口形式

```plaintext
download_url?imageMogr2/format/<Format>
					   /cgif/<FrameNumber>
					   /interlace/<Mode>
```

>请忽略上面的空格与换行符。
## 参数说明

| 参数                 | 描述                                                         |
| -------------------- | ------------------------------------------------------------ |
| download_url | 文件的访问链接，具体构成为`<BucketName-APPID>.cos.<picture region>.<domain>.com/<picture name>`，<br>例如`examplebucket-1250000000.cos.ap-shanghai.myqcloud.com/picture.jpeg`。 |
| /format/&lt;Format>  | 格式转换：目标缩略图的图片格式可为：jpg，bmp，gif，png，webp，yjpeg 等，其中 yjpeg 为数据万象针对 jpeg 格式进行的优化，本质为 jpg 格式；缺省为原图格式。 |
| /cgif/&lt;FrameNumber&gt;  | gif 格式优化：只针对原图为 gif 格式的图片进行优化，降帧降颜色。分为以下两种情况：<li>FrameNumber=1，则按照默认帧数30处理，如果图片帧数大于该帧数则截取。<li>FrameNumber 取值( 1,100 ]，则将图片压缩到指定帧数 （FrameNumber）。 |
| /interlace/&lt;Mode> | 输出为渐进式 jpg 格式。Mode 可为0或1：<br><li>0：表示不开启渐进式<br><li>1：表示开启渐进式<br>该参数仅在输出图片格式为 jpg 格式时有效。如果输出非 jpg 图片格式，会忽略该参数，默认值0。 |


## 实际案例

将 jpeg 格式的原图片转换为 png 格式：

```plaintext
http://examples-1251000004.cos.ap-shanghai.myqcloud.com/sample.jpeg?imageMogr2/format/png
```

