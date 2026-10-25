# dist/

`homekey-standin-com_ts_launcher.apk` —— 实测通过的构建产物，**版本 102**。

这个包是为小米电视（包名白名单机制）编的，里面预置了具体参数：

- 包名：`com.ts.launcher`
- Activity：`com.gathin.tvhome.MainActivity`（沿用某个旧桌面组件名，改包名没用，必须连组件名一起换）
- 跳转目标：`app.orchard.tv/.MainActivity`

装之前先改成你自己的目标桌面：

```bash
# 1. 装上
adb install -r homekey-standin-com_ts_launcher.apk

# 2. 设成默认桌面
adb shell cmd package set-home-activity --user 0 \
  com.ts.launcher/com.gathin.tvhome.MainActivity
```

换个电视、换个桌面的话，别用这个包，自己编一个：

```bash
./build.sh --pkg <包名> --activity <组件名> --target-pkg <目标桌面包名> --target-class <目标Activity>
```

默认参数下 Activity 是 `com.homekey.standin.MainActivity`，设默认桌面时别写成别的。
