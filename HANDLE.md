
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
