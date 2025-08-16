# IMS_VAROS
stop some official schedulers of ColorOS/RealmeUI


模块功能：
有时你发现使用第三方调度（主要分为两类：CPU调频调度 CPU线程放置）功耗更高，帧率更不稳定，原因之一是：官方的调度在干扰第三方调度
模块用于屏蔽ColorOS官方调度，尝试阻止其干扰第三方调度
（你可以在模块目录的MODS/Scheduler.cfg里加大去除官调的力度，但需注意里面的说明）

注意：安装模块前，一定要安装救砖模块
卸载模块即可恢复模块所做所有改动（除了被清空的应用增强服务或游戏助手数据）

适用范围：
适用于ColorOS12/13/14/15或RelameUI3.0/4.0/5.0/6.0




模块效果检测：
官方调度有多个方面，而IMS_VAROS模块主要屏蔽了两个方面：
①CPU调频调度 ②CPU线程放置

以下是检测这两个方面是否被屏蔽的办法：

【准备：关闭所有[线程放置模块]，关闭任何[调频调度（如SceneHP ywx FAS-RS）]，并重启设备】

①检测官方[CPU线程放置]是否被屏蔽
  【首先】，打开Scene的CPU控制页面，注意【顶层的应用】右侧的字符，它意味着处于顶层的应用被分配的CPU核心为0到7号核心
  【然后】，在应用中打开Scene的线程监视器。[COMM列]是[线程名]，横着看，[CPUS列]是每个线程[被分配的CPU核心]。注意，此时应用就处于顶层，即它就是【顶层的应用】，所以它内部的每一个线程都应该被分配【顶层的应用】规定的CPU核心
  【最后】，对比【顶层的进程】规定的CPU核心，是否与线程监视器上前10个线程【CPUS列】所显示的被分配的CPU核心一致。
  如果完全一致，则官方[CPU线程放置]屏蔽成功
  如果不完全一致，也不一定表明未能屏蔽，可能来自内核，但不影响第三方线程放置


②检测官方[CPU调频调度]是否被屏蔽
  进入Scene的CPU控制页面，任意调整所有【最小频率】【最大频率】【调速器】，然后反复下拉控制中心，切换应用，滑动桌面，进出游戏，再回到该页面。
  如果以上所有被调整的参数都没有改变，则官方[CPU调频调度]屏蔽成功




### **Module Functionality:**  
Sometimes, you may find that using third-party schedulers (primarily divided into two categories: **CPU frequency scheduling** and **CPU thread placement**) results in higher power consumption and less stable frame rates. One reason for this is that the **official scheduler interferes with third-party schedulers**.  

This module is designed to **block ColorOS's official scheduler**, attempting to prevent it from disrupting third-party schedulers.  
*(You can increase the blocking intensity in `MODS/Scheduler.cfg` under the module directory, but please note the instructions inside.)*  

⚠ **Note:** Before installing this module, **you must install the "Brick Recovery Module"**.  
Uninstalling this module will revert all changes made by it *(except for cleared data in "com.oplus.cosa" or "com.oplus.games")*.  

---  

### **Compatibility:**  
- **ColorOS 12/13/14/15**  
- **Realme UI 3.0/4.0/5.0/6.0**  

---  

### **Module Effectiveness Check:**  
The official scheduler operates in multiple aspects, but the **IMS_VAROS module primarily blocks two:**  
1. **CPU Frequency Scheduling**  
2. **CPU Thread Placement**  

Here’s how to check if these two aspects are successfully blocked:  

#### **Preparation:**  
- **Disable all [thread placement modules].**  
- **Disable any [frequency schedulers (e.g., SceneHP, ywx, FAS-RS)].**  
- **Reboot your device.**  

---  

#### **① Check if Official [CPU Thread Placement] is Blocked:**  
1. **First**, open **Scene’s CPU Control Page** and observe the **character on the right side of the [Top App]**. This indicates the CPU cores (0-7) assigned to the top app.  
2. **Then**, open **Scene’s Thread Monitor** while the app is in the foreground.  
   - The **[COMM Column]** shows the **thread names**.  
   - The **[CPUS Column]** shows the **CPU cores assigned to each thread**.  
   - Since the app is in the foreground, **every thread should be assigned the cores specified for the [Top App]**.  
3. **Finally**, compare whether the **CPU cores assigned to the [Top App]** match the **[CPUS Column]** for the first 10 threads in the Thread Monitor.  
   - **If they match completely** → Official [CPU Thread Placement] is successfully blocked.  
   - **If not fully matched**, it doesn’t necessarily mean blocking failed—it could be due to kernel behavior, but this won’t affect third-party thread placement.  

---  

#### **② Check if Official [CPU Frequency Scheduling] is Blocked:**  
1. Go to **Scene’s CPU Control Page** and adjust:  
   - **[Minimum Frequency]**  
   - **[Maximum Frequency]**  
   - **[Governor]**  
2. Then, perform the following actions repeatedly:  
   - Pull down the **Quick Settings panel**.  
   - Switch between apps.  
   - Swipe on the home screen.  
   - Enter and exit a game.  
3. Return to the **CPU Control Page**.  
   - **If all adjusted parameters remain unchanged** → Official [CPU Frequency Scheduling] is successfully blocked.  

