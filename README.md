# KSDK2_MCIMXRT1052

本项目为RT1052的IAR模板工程，采用了类似[KSDK2_KV58-IAR-project](https://github.com/AlexYzhov/KSDK2_KV58-IAR-project)  repo里的文件组织结构。

硬件上，本工程基于我和网友Stackoverflow共同开发的**SphinxEVK** iMX RT1052开发板，其中片外存储器主要使用的是Winbond W25Q256JVEQ，但同时也预留了SDRAM和同时兼容Hyperflash、OctaFlash的FlexSPI接口。

软件上，本工程基于MCUXpressoSDK2.3.1驱动(**/Library/MCUXpressoSDK**)，同时打包封装了CMSIS数学库、CMSIS-DSP库(**/Library/CMSIS**)，并且添加了一些NXP提供的中间件软件(**/Middleware**)。本工程通过对GPIO_B0_15进行编程，实现了LED闪烁。

为了节约编译时间，IAR工程中并未添加所有的.c文件。如需用到其他外设驱动功能，请依照路径自行添加源代码文件。

注：下载算法使用了开发者自己编写的flashloader，目前仅适配Winbond W25QxxxJV系列。如需挂载其他型号的QSPI-Flash，请参照[IMXRT_IARFlashloader](https://github.com/AlexYzhov/IMXRT_IARFlashloader)里的文件，添加设备描述和FlexBus LUT表，自行编译对应的flashloader。

**/App/:** 用于放置自己编写的应用程序。

**/Board/:** 用于存放板级支持文件，比如管脚复用、时钟初始化，以及外设驱动配置。

**/Drivers/:** 用于存放自己编写的硬件驱动程序，如LCD、陀螺仪，etc。

**/iar/:** IAR工程根目录$PROJ_DIR$所在地址。存放了IAR工程的配置文件，以及工程中使用到的Linker配置文件和flashloader。

**/Library/:** NXP和ARM提供的驱动库，绝大多数文件ReadOnly。

**/Middleware/:** NXP提供的中间件文件。

**/SEGGER/:** SEGGER提供的RTT文件，可用于在线调试。

**/Xip/:** iMX.RT片外执行必须依赖的一些文件。除非特别了解，否则不要修改。