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
   比如模拟上的开机时间
   ![image](https://github.com/user-attachments/assets/f02af19d-7400-43bf-ba99-619dde383ee4)


## 完成后，请删除 /data/bootchart/enabled 以防止每次开机都收集数据。

# 对比两次开始时间的差异
1. 第一次开机后执行./grab-bootchart.sh 后开机资料抓到了log目录下，重命名为log1
2. 第二次开机后执行./grab-bootchart.sh 后开机资料抓到了log目录下，重命名为log2
3. 执行 ./compare-bootcharts.py log1 log2 比较开机时间差异
   ![image](https://github.com/user-attachments/assets/f8f009de-ad6c-4d01-b5eb-c15bfd9b182d)

# 参考
   https://source.android.com/docs/core/perf/boot-times?hl=zh-cn#bootchart
   1. 脚本工具都在原生代码目录下：
   system/core/init/grab-bootchart.sh
   system/core/init/compare-bootcharts.py
   2. 高版本的ubuntu没法用apt直接安装bootchart,所以需要自己git clone,并设置grab-bootchart.sh中pybootchartgui的路径，而此工程中提供的正式基于此做了调整，直接下载后有使用。
