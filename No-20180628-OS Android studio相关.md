android studio SDK文件路径：
/Users/ganjinjin/Library/Android/sdk

Android studio 卸载命令：
rm -Rf /Applications/Android\ Studio.app
rm -Rf ~/Library/Preferences/AndroidStudio*
rm ~/Library/Preferences/com.google.android.studio.plist
rm -Rf ~/Library/Application\ Support/AndroidStudio*
rm -Rf ~/Library/Logs/AndroidStudio*
rm -Rf ~/Library/Caches/AndroidStudio*

mac查看隐藏文件：
shift + cmd + .

Android studio 在Mac上遇到的诡异问题：
保存设置无效，设置过的项，重新打开又恢复了原样

mac下，studio清除缓存方法：
根目录下，`shift + cmd + .` 显示隐藏文件，删除`.android` 和 `.gradle`文件夹，重新安装studio即可。