# bootchart
Android Boot Time 分析工具

# 使用方法
1. 下载工具到Linux平台
   git clone git@github.com/bootchart.git bootchart
2. cd bootchart
3. adb 连接到Android设备
4. 执行 adb shell 'touch /data/bootchart/enabled'
5. 重启 adb reboot
6. 检查设备的 /data/bootchart/ 目录下生成的资料
   bootchart.tgz
   header
   proc_diskstats.log
   proc_ps.log
   proc_stat.log
7. Linux平台执行 ./grab-bootchart.sh 会自动把设备上的bootchart抓下来并生成 bootchart.png
8. 分析 bootchart.png 的时间信息

## 完成后，请删除 /data/bootchart/enabled 以防止每次开机都收集数据。

# 对比两次开始时间的差异
1. 把两次开机的bootchart资料抓取到本地，比如log1/log2两个目录下
2. 执行 ./compare-bootcharts.py log1 log2

# 参考
https://source.android.com/docs/core/perf/boot-times?hl=zh-cn#bootchart
