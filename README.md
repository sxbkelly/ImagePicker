
# 使用方式:

1、如何在项目中引入该图片加载库：
```
                //gradle版本在3.0以上引入此行
                implementation 'com.lcw.library:imagepicker:2.2.7'
```
2、如何自定义图片加载器（不定死框架，让框架更加灵活，需要去实现ImageLoader接口即可，如果需要显示视频，优先推荐Glide加载框架，可以参考Demo实现）：
```
            public class GlideLoader implements ImageLoader {
                //to do something 可以参考Demo用法
                
            }
```
3、一行代码调用：
```
                ImagePicker.getInstance()
                        .setTitle("标题")//设置标题
                        .showCamera(true)//设置是否显示拍照按钮
                        .showImage(true)//设置是否展示图片
                        .showVideo(true)//设置是否展示视频
                        .filterGif(false)//设置是否过滤gif图片
                        .setSingleType(true)//设置图片视频不能同时选择
                        .setMaxCount(9)//设置最大选择图片数目(默认为1，单选)
                        .setImagePaths(mImageList)//保存上一次选择图片的状态，如果不需要可以忽略
                        .setImageLoader(new GlideLoader())//设置自定义图片加载器
                        .start(MainActivity.this, REQUEST_SELECT_IMAGES_CODE);//REQEST_SELECT_IMAGES_CODE为Intent调用的requestCode
```

4、如何获取选中的图片集合：
```
                @Override
                protected void onActivityResult(int requestCode, int resultCode, Intent data) {
                    if (requestCode == REQUEST_SELECT_IMAGES_CODE && resultCode == RESULT_OK) {
                        List<String> imagePaths = data.getStringArrayListExtra(ImagePicker.EXTRA_SELECT_IMAGES);
                    }
                }
```

 

