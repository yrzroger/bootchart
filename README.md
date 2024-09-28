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
   ![image](https://github.com/user-attachments/assets/4f14f087-6642-4212-881d-14afba9053c9)
7. Linux平台执行 ./grab-bootchart.sh 会自动把设备上的bootchart抓下来并生成 bootchart.png
   ![image](https://github.com/user-attachments/assets/aee035cb-0b56-4d8e-b9a2-ebf65b28ae88)
9. 分析 bootchart.png 的时间信息

## 完成后，请删除 /data/bootchart/enabled 以防止每次开机都收集数据。

# 对比两次开始时间的差异
1. 第一次开机后执行./grab-bootchart.sh 后开机资料抓到了log目录下，重命名为log1
2. 第二次开机后执行./grab-bootchart.sh 后开机资料抓到了log目录下，重命名为log2
3. 执行 ./compare-bootcharts.py log1 log2 比较开机时间差异
   ![image](https://github.com/user-attachments/assets/f8f009de-ad6c-4d01-b5eb-c15bfd9b182d)

# 参考
   https://source.android.com/docs/core/perf/boot-times?hl=zh-cn#bootchart
