
# 进程查找 & 删除
pgrep -fl uxplay
pkill -f uxplay


# 打包
dylibbundler -od -b -x uxplay -d ./libs/ -p @executable_path/libs
mkdir gst-plugins
cp /opt/homebrew/lib/gstreamer-1.0/*.dylib gst-plugins
cp -r /opt/homebrew/Cellar/gstreamer/1.26.1/libexec .
DYLD_LIBRARY_PATH=libs GST_PLUGIN_PATH=gst-plugins ./uxplay

# 查看依赖
oTool -L uxplay


# h264 格式观察
* 画面变动，文件内存变动大， 画面禁止，文件内存变动小
* 可以覆盖原文件名
* -vdmp 不支持传未创建的目录，单支持传未创建的文件 ./uxplay -vdmp ~/Downloads/video
* -fps 1 极大降低文件大小
* 设置了 -vdmp [n]  这个n好像会导致视频数据保存有问题？
* 文件夹管理器无法实时看文件大小变化，可以切换目录来实现， 或则用命令 ls -lh video.h264